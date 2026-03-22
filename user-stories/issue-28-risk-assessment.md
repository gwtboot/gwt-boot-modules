# Issue #28: Risk Assessment and Upgrade Strategy

---

## 1. Risk Matrix

| # | Dependency | Upgrade | Risk Level | Risk Description |
|---|---|---|---|---|
| 1 | GWT Core | 2.10.0 -> 2.13.0 | **MEDIUM** | Foundation of everything. 3 minor versions. GWT has good backward compat, but needs validation. May require Java 11+. |
| 2 | DominoUI | 1.0.0-RC13 -> 2.1.0 | **HIGH** | Full major version change from RC to stable 2.x. API breakage expected. Maven coordinates or GWT module names may have changed. |
| 3 | Elemento | 1.0.10 -> 2.4.9 | **HIGH** | Complete rewrite in 2.x. Package names, API, and GWT module names changed. Also affects RxGWT starter (uses special Elemento version). |
| 4 | Domino REST | 1.0.0-RC7 -> 2.0.0 | **HIGH** | Major version jump. Coordinate and API changes likely. |
| 5 | Dagger | 2.43.2 -> 2.59.2 | **HIGH** | Google may have dropped the `dagger-gwt` artifact. If so, the Dagger2 starter cannot be upgraded and may need deprecation. |
| 6 | GWTBootstrap3 | 0.9.4 -> 1.0.1 | **MEDIUM** | Major version but within same ecosystem. Extras version diverges (1.0.2). |
| 7 | GWT Material | 2.6.1 -> 2.8.5 | **LOW** | Minor version bump within same major. |
| 8 | JAX-RS API | 2.1 -> 2.1.1 | **LOW** | Patch release. |
| 9 | maven-compiler-plugin | 3.7.0 -> 3.13.0 | **LOW** | Build plugin, well-tested. |
| 10 | DnComponents | 2.4.2 -> skip | **NONE** | Not upgrading (only alpha available). |

---

## 2. High-Risk Items: Detailed Analysis

### 2.1 DominoUI (1.0.0-RC13 -> 2.1.0)

**What could break:**
- The `domino-ui` artifact may have changed its GWT module name
- The `domino-ui` sources classifier may no longer be needed (or may not exist)
- API classes and packages likely restructured in 2.x
- Transitive dependencies may have changed

**Investigation needed before upgrade:**
1. Check DominoUI 2.x release notes / migration guide
2. Verify `org.dominokit:domino-ui:2.1.0` exists on Maven Central
3. Verify `org.dominokit:domino-ui:2.1.0:sources` classifier exists
4. Check the GWT module name in DominoUI 2.x

**Affected files:**
- `gwt-boot-dependencies/pom.xml` (version property)
- `gwt-boot-starters/gwt-boot-starter-ui-domino/pom.xml` (dependency declarations)
- `gwt-boot-starters/gwt-boot-starter-ui-domino/src/main/resources/.../DominoUIStarter.gwt.xml` (inherits)

**Fallback:** If DominoUI 2.x is incompatible, keep at `1.0.0-RC13` and
document in the issue. Open a separate follow-up issue.

---

### 2.2 Elemento (1.0.10 -> 2.4.9)

**What could break:**
- Elemento 2.x is a ground-up rewrite
- Java package changed from `org.jboss.elemento` to potentially different structure
- GWT module name likely changed
- The special `1.0.10-gwtcom` version used by RxGWT starter has no 2.x equivalent

**Investigation needed before upgrade:**
1. Check Elemento 2.x GitHub/release notes
2. Verify new GWT module name
3. Check if RxGWT (`com.intendia.gwt.rxgwt2:rxgwt:2.3`) is compatible with Elemento 2.x
4. If not compatible, the RxGWT starter may need to keep the old Elemento version override

**Affected files:**
- `gwt-boot-dependencies/pom.xml` (version property)
- `gwt-boot-starters/gwt-boot-starter-elemento-core/pom.xml`
- `gwt-boot-starters/gwt-boot-starter-elemento-core/src/main/resources/.../ElementoCoreStarter.gwt.xml`
- `gwt-boot-starters/gwt-boot-starter-rxgwt/pom.xml` (special version override)

**Fallback:** Upgrade Elemento in the elemento-core starter only. Keep the
RxGWT starter on the old version with its existing override.

---

### 2.3 Domino REST (1.0.0-RC7 -> 2.0.0)

**What could break:**
- Artifact coordinates may have changed
- API restructured for 2.0.0 stable release
- `domino-rest-shared` artifact may have been merged or removed

**Investigation needed before upgrade:**
1. Verify all three artifacts exist at 2.0.0: `domino-rest-client`,
   `domino-rest-processor`, `domino-rest-shared`
2. Check if GWT module names changed
3. Review Domino REST 2.0 changelog

**Affected files:**
- `gwt-boot-dependencies/pom.xml` (version property + dependency entries)
- `gwt-boot-starters/gwt-boot-starter-domino-rest/pom.xml`
- `gwt-boot-starters/gwt-boot-starter-domino-rest/src/main/resources/.../DominoRestStarter.gwt.xml`

**Fallback:** Keep at `1.0.0-RC7` if 2.0.0 introduces breaking coordinate changes.

---

### 2.4 Dagger GWT (2.43.2 -> 2.59.2)

**What could break:**
- Google has been de-emphasizing GWT support in Dagger
- The `dagger-gwt` artifact may not exist at version 2.59.2
- If `dagger-gwt` was removed, the entire `gwt-boot-starter-dagger2` becomes broken

**Investigation needed before upgrade:**
1. Check Maven Central for `com.google.dagger:dagger-gwt:2.59.2`
2. If it does not exist, find the last version that includes `dagger-gwt`
3. Consider deprecating the Dagger2 starter if GWT support was dropped

**Affected files:**
- `gwt-boot-dependencies/pom.xml` (version property)
- `gwt-boot-starters/gwt-boot-starter-dagger2/pom.xml`

**Fallback:** Keep at `2.43.2` or upgrade to the last version that includes
`dagger-gwt`. Document limitation.

---

## 3. Recommended Upgrade Strategy

Given the mix of risk levels, the recommended approach is **incremental
upgrades with validation gates**:

```
Phase 1: GWT Core (2.10.0 -> 2.13.0)
  |
  +-- GATE: mvn clean install passes?
  |     YES -> proceed
  |     NO  -> investigate GWT 2.13.0 compat issues
  |
Phase 2: Low-risk upgrades (GWT Material, JAX-RS API, plugins)
  |
  +-- GATE: mvn clean install passes?
  |     YES -> proceed
  |     NO  -> revert individual problem upgrade
  |
Phase 3: Medium-risk upgrades (GWTBootstrap3)
  |
  +-- GATE: mvn clean install passes?
  |
Phase 4: High-risk upgrades (one at a time)
  |
  +-- 4a: Dagger (verify artifact exists first)
  +-- 4b: Elemento (check API/module changes)
  +-- 4c: DominoUI (check migration path)
  +-- 4d: Domino REST (check coordinate changes)
  |
  +-- GATE: mvn clean install passes after each?
  |
Phase 5: Cleanup and documentation
```

---

## 4. Dependencies Between Upgrades

Some upgrades are coupled and must be considered together:

```
GWT Core 2.13.0
  |
  +-- All other upgrades depend on this
  |
Elemento 2.x
  |
  +-- Affects: gwt-boot-starter-elemento-core
  +-- Affects: gwt-boot-starter-rxgwt (uses special Elemento version)
  +-- May affect: gwt-boot-starter-ui-domino (DominoUI may depend on Elemento)
  |
DominoUI 2.x
  |
  +-- May require: Elemento 2.x (DominoUI 2.x likely depends on Elemento 2.x)
  +-- May require: Domino REST 2.x (same ecosystem)
  |
Domino REST 2.x
  |
  +-- Part of Dominokit ecosystem (coupled with DominoUI)
```

**Recommendation:** Upgrade the entire Dominokit ecosystem (DominoUI + Domino
REST + Elemento) together in a single phase, as they are tightly coupled.

---

## 5. Items NOT Being Upgraded (with justification)

| Dependency | Current | Available | Reason |
|---|---|---|---|
| DnComponents | `2.4.2` | `3.0.0-alpha-3` | Alpha release, not stable |
| Vue GWT | `1.0.1` | `1.0.1` | No newer version available |
| RestyGWT | `2.2.7` | `2.2.7` | No newer version available |
| GWT Mockito | `1.1.9` | `1.1.9` | No newer version available |
| GWT EventBinder | `1.1.0` | `1.1.0` | No newer version available |
| Gin | `3.0.0` | `3.0.0` | No newer version available |
| RxGWT | `2.3` | `2.3` | No newer version available |
| RxJava2 GWT | `2.2.20-gwt1` | `2.2.20-gwt1` | No newer version available |
| javax.inject | `1` | `1` | No newer version available |

---

## 6. Potential Deprecation Candidates

Based on project activity and ecosystem trends, these starters may warrant
deprecation consideration during this upgrade cycle:

| Starter | Reason |
|---|---|
| `gwt-boot-starter-dagger2` | Dagger may have dropped GWT support |
| `gwt-boot-starter-gin` | Gin is no longer maintained (last release years ago) |
| `gwt-boot-starter-rxgwt` | RxGWT depends on special Elemento build; may be unmaintained |
| `gwt-boot-starter-ui-vue-gwt` | Vue GWT appears unmaintained (no releases) |

**Note:** Deprecation is a separate decision from this upgrade issue. These are
flagged for awareness only.

---

## 7. Pre-Implementation Checklist

Before starting any code changes, complete these investigations:

- [ ] Verify `com.google.gwt:gwt:2.13.0` BOM exists on Maven Central
- [ ] Read GWT 2.11.0, 2.12.0, 2.13.0 release notes for breaking changes
- [ ] Check GWT 2.13.0 minimum Java version requirement
- [ ] Verify `com.google.dagger:dagger-gwt:2.59.2` exists on Maven Central
- [ ] Check DominoUI 2.x migration guide / release notes
- [ ] Check Elemento 2.x migration guide / release notes
- [ ] Verify Domino REST 2.0.0 artifact coordinates on Maven Central
- [ ] Check GWTBootstrap3 1.0.x release notes
- [ ] Verify `net.ltgt.gwt.maven:gwt-maven-plugin` latest version
- [ ] Determine if Java 11+ is required for any of the upgraded dependencies
