# Issue #28: Update GWT Boot Dependencies to Latest Versions

## Implementation Plan

**Issue:** https://github.com/gwtboot/gwt-boot-modules/issues/28
**Date:** 2026-03-22
**Scope:** Update all dependencies in gwt-boot-modules to their latest stable versions

---

## 1. Overview

GWT Boot Modules is a Maven multi-module project providing "starter" dependency
descriptors for GWT. All dependency versions are centrally managed in a single
file: `gwt-boot-dependencies/pom.xml`. This makes the upgrade process
well-contained -- version properties in that one file control the entire project.

**Key file to modify:** `gwt-boot-dependencies/pom.xml` (properties + dependencyManagement)

---

## 2. Implementation Phases

The upgrade should be done in **5 sequential phases**, each resulting in a
separate commit (or PR) to allow isolated testing and easy rollback.

### Phase 1: Core GWT Upgrade (HIGH PRIORITY)

**Goal:** Upgrade GWT from 2.10.0 to 2.13.0

**Changes in `gwt-boot-dependencies/pom.xml`:**

| Property | Current | Target |
|---|---|---|
| `gwt.version` | `2.10.0` | `2.13.0` |
| `gwt-maven-plugin.version` | `1.0.1` | Check compatibility with GWT 2.13.0 |

**Rationale:** GWT is the foundation. All other libraries depend on GWT
compatibility. This must be done first and validated before proceeding.

**Risks:**
- GWT 2.13.0 is a major jump (3 minor versions). Check the GWT release notes
  for breaking changes.
- The GWT BOM import (`com.google.gwt:gwt`) auto-manages `gwt-user`, `gwt-dev`,
  `gwt-codeserver`, `gwt-servlet` -- these will all update automatically.
- Third-party libraries may not yet be compatible with GWT 2.13.0.

**Validation:**
- `mvn clean install` from root must succeed
- Verify the GWT BOM import still resolves correctly with the new coordinates

---

### Phase 2: UI Framework Upgrades (MEDIUM PRIORITY)

**Goal:** Upgrade GWT UI frameworks to latest stable versions

**Changes in `gwt-boot-dependencies/pom.xml`:**

| Property | Current | Target | Notes |
|---|---|---|---|
| `gwt-bootstrap3.version` | `0.9.4` | `1.0.1` | Major version bump. Check API changes. `gwtbootstrap3-extras` latest is `1.0.2` -- versions diverge, may need separate property. |
| `gwt-material.version` | `2.6.1` | `2.8.5` | Minor bump, lower risk |
| `gwt-dominoui.version` | `1.0.0-RC13` | `2.1.0` | **Major version bump.** High risk of API breakage. Check migration guide. |
| `dncomponents.version` | `2.4.2` | `2.4.2` (keep) | Latest stable is `3.0.0-alpha-3` which is alpha -- do NOT upgrade |
| `vue-gwt.version` | `1.0.1` | `1.0.1` (keep) | No newer stable version found |

**Special handling for GWTBootstrap3:**
The `gwtbootstrap3` artifact latest is `1.0.1` but `gwtbootstrap3-extras` latest
is `1.0.2`. If these are published from different release cycles, introduce a
second property `gwt-bootstrap3-extras.version` or verify that `1.0.1` works
for both.

**Special handling for DominoUI:**
The jump from `1.0.0-RC13` to `2.1.0` is a full major version change. This
requires:
1. Checking if the Maven coordinates changed
2. Checking if the GWT module name in `.gwt.xml` changed
3. Checking if the `domino-ui` sources classifier artifact still exists
4. Updating `gwt-boot-starters/gwt-boot-starter-ui-domino/pom.xml` if
   dependency coordinates changed
5. Updating `DominoUIStarter.gwt.xml` if module inherits changed

**Validation:**
- `mvn clean install` from root
- Verify each affected starter module resolves its dependencies correctly

---

### Phase 3: Library/Framework Upgrades (MEDIUM PRIORITY)

**Goal:** Upgrade non-UI libraries

**Changes in `gwt-boot-dependencies/pom.xml`:**

| Property | Current | Target | Notes |
|---|---|---|---|
| `gwt-dagger2.version` | `2.43.2` | `2.59.2` | Check if `dagger-gwt` artifact still exists at 2.59.2. Dagger dropped GWT support in some versions. |
| `gwt-restygwt.version` | `2.2.7` | `2.2.7` (keep) | No newer version detected by Maven. Verify on Maven Central. |
| `rs-api.version` | `2.1` | `2.1.1` | Patch bump, safe |
| `gwt-elemento.version` | `1.0.10` | `2.4.9` | **Major version bump.** Check if groupId/artifactId changed. Elemento 2.x may have moved to `org.jboss.elemento:elemento-core` or different coordinates. |
| `gwt-domino-rest.version` | `1.0.0-RC7` | `2.0.0` | **Major version bump.** Check coordinate changes. |
| `rx-gwt.version` | `2.3` | `2.3` (keep) | No newer version available |
| `rx-java-gwt.version` | `2.2.20-gwt1` | `2.2.20-gwt1` (keep) | No newer version available |
| `gwt-mockito.version` | `1.1.9` | `1.1.9` (keep) | No newer version detected |
| `gwt-eventbinder.version` | `1.1.0` | `1.1.0` (keep) | No newer version detected |
| `gwt-gin.version` | `3.0.0` | `3.0.0` (keep) | No newer version detected |
| `inject-api.version` | `1` | `1` (keep) | `javax.inject` has not changed |

**Special handling for Elemento:**
Elemento 2.x is a complete rewrite. The jump from `1.0.10` to `2.4.9` likely
involves:
1. Changed Java package names
2. Changed GWT module names (affects `.gwt.xml` files)
3. Changed API surface

This also affects `gwt-boot-starter-rxgwt` which uses a special
`elemento-core` version (`1.0.10-gwtcom`). Verify if RxGWT is compatible
with Elemento 2.x, or if the special version override must be retained.

**Special handling for Dagger:**
Google Dagger may have removed the `dagger-gwt` artifact in newer versions.
Verify on Maven Central that `com.google.dagger:dagger-gwt:2.59.2` exists
before upgrading. If it was removed, this starter may need to be deprecated or
reworked.

**Special handling for Domino REST:**
The jump from `1.0.0-RC7` to `2.0.0` is a major release. Check:
1. Whether `domino-rest-client`, `domino-rest-processor`, `domino-rest-shared`
   artifacts still exist at 2.0.0
2. Any coordinate or package changes

**Validation:**
- `mvn clean install` from root
- Check dependency tree for conflicts: `mvn dependency:tree`

---

### Phase 4: Build Plugin and Infrastructure Upgrades (LOW PRIORITY)

**Goal:** Upgrade Maven plugins and build infrastructure

**Changes in `gwt-boot-dependencies/pom.xml`:**

| Plugin/Tool | Current | Target | Notes |
|---|---|---|---|
| `maven-compiler-plugin` | `3.7.0` | `3.13.0` (latest) | Safe upgrade |
| `gwt-maven-plugin` | `1.0.1` | Verify latest | `net.ltgt.gwt.maven:gwt-maven-plugin` |
| Java source/target | `1.8` | Consider `11` | GWT 2.13.0 may require Java 11+. Check GWT release notes. |

**Changes in root `pom.xml`:**
- Update `nexus-staging-maven-plugin` if newer version available
- Update `maven-release-plugin`, `maven-gpg-plugin`, `maven-source-plugin`,
  `maven-javadoc-plugin` in the `release` profile

**Changes in `.github/workflows/maven.yml`:**
- If Java target is raised to 11+, update CI JDK version accordingly

**Validation:**
- `mvn clean install` from root
- `mvn clean install -Prelease` (dry run, no deploy) to verify release profile

---

### Phase 5: Cleanup and Documentation (LOW PRIORITY)

**Goal:** Post-upgrade housekeeping

**Tasks:**
1. Update `README.md` if any starter usage instructions changed
2. Remove `pom.xml.versionsBackup` (leftover from previous `mvn versions:set`)
3. Verify all `.gwt.xml` module descriptors still have correct `<inherits>` entries
4. Run `mvn dependency:analyze` to check for unused/undeclared dependencies
5. Run OWASP dependency check if applicable: `mvn org.owasp:dependency-check-maven:check`
6. Create CHANGELOG entry

---

## 3. File Change Matrix

| File | Phase | Changes |
|---|---|---|
| `gwt-boot-dependencies/pom.xml` | 1-4 | Version properties, dependencyManagement entries, pluginManagement |
| `gwt-boot-starters/gwt-boot-starter-ui-domino/pom.xml` | 2 | Possible dependency coordinate changes |
| `gwt-boot-starters/gwt-boot-starter-rxgwt/pom.xml` | 3 | Elemento version override may change |
| `gwt-boot-starters/gwt-boot-starter-elemento-core/pom.xml` | 3 | Possible coordinate changes |
| `gwt-boot-starters/gwt-boot-starter-domino-rest/pom.xml` | 3 | Possible coordinate changes |
| `gwt-boot-starters/gwt-boot-starter-dagger2/pom.xml` | 3 | Verify dagger-gwt artifact still exists |
| `gwt-boot-starters/gwt-boot-starter-ui-gwtbootstrap3/pom.xml` | 2 | Possible if extras version diverges |
| Various `*.gwt.xml` files | 2-3 | If GWT module names changed in upgraded libs |
| `.github/workflows/maven.yml` | 4 | JDK version if Java target changes |
| `pom.xml` (root) | 4 | Plugin versions in release profile |
| `gwt-boot-starters/gwt-boot-starter-parent/pom.xml` | 4 | Java source/target if raised |
| `README.md` | 5 | Usage instructions if needed |

---

## 4. Testing Strategy

### Per-Phase Validation
After each phase, run:
```bash
mvn clean install
mvn dependency:tree -Dverbose
```

### Full Validation (after all phases)
```bash
# Build everything
mvn clean install

# Check for dependency conflicts
mvn dependency:tree -Dverbose | grep "omitted for conflict"

# Analyze dependencies
mvn dependency:analyze

# Security check (optional)
mvn org.owasp:dependency-check-maven:check
```

### Manual Verification
- Create a sample GWT project using `gwt-boot-starter-parent` as parent
- Add one or two starters as dependencies
- Verify the project compiles and the GWT compiler runs successfully

---

## 5. Rollback Strategy

Each phase is a separate commit. If a phase introduces incompatibilities:
1. Revert the commit for that phase
2. Document the incompatibility in the issue
3. Proceed with remaining phases that are independent
4. Open a follow-up issue for the blocked upgrade

---

## 6. Estimated Effort

| Phase | Effort | Risk |
|---|---|---|
| Phase 1: Core GWT | 1-2 hours | Medium |
| Phase 2: UI Frameworks | 2-4 hours | High (DominoUI 2.x) |
| Phase 3: Libraries | 2-4 hours | High (Elemento 2.x, Dagger GWT) |
| Phase 4: Build Plugins | 1 hour | Low |
| Phase 5: Cleanup/Docs | 1 hour | Low |
| **Total** | **7-12 hours** | |
