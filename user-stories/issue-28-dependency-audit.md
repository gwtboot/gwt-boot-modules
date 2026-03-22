# Issue #28: Dependency Audit

## Current vs. Latest Stable Versions

**Source:** `mvn versions:display-dependency-updates` run on 2026-03-22
**File governing all versions:** `gwt-boot-dependencies/pom.xml`

---

## Direct Dependencies (Managed in gwt-boot-dependencies)

### Core GWT

| Property | GroupId:ArtifactId | Current | Latest | Delta | Action |
|---|---|---|---|---|---|
| `gwt.version` | `com.google.gwt:gwt` (BOM) | `2.10.0` | `2.13.0` | 3 minor | **Upgrade** |
| -- | `org.gwtproject:gwt-user` | `2.10.0` | `2.13.0` | (via BOM) | Auto |
| -- | `org.gwtproject:gwt-dev` | `2.10.0` | `2.13.0` | (via BOM) | Auto |
| -- | `org.gwtproject:gwt-codeserver` | `2.10.0` | `2.13.0` | (via BOM) | Auto |
| -- | `org.gwtproject:gwt-servlet` | `2.10.0` | `2.13.0` | (via BOM) | Auto |

### UI Frameworks

| Property | GroupId:ArtifactId | Current | Latest | Delta | Action |
|---|---|---|---|---|---|
| `gwt-bootstrap3.version` | `org.gwtbootstrap3:gwtbootstrap3` | `0.9.4` | `1.0.1` | Major | **Upgrade** |
| `gwt-bootstrap3.version` | `org.gwtbootstrap3:gwtbootstrap3-extras` | `0.9.4` | `1.0.2` | Major | **Upgrade** (note: version diverges from main artifact) |
| `gwt-material.version` | `com.github.gwtmaterialdesign:gwt-material` | `2.6.1` | `2.8.5` | Minor | **Upgrade** |
| `gwt-material.version` | `com.github.gwtmaterialdesign:gwt-material-themes` | `2.6.1` | `2.8.5` | Minor | **Upgrade** |
| `gwt-material.version` | `com.github.gwtmaterialdesign:gwt-material-addins` | `2.6.1` | `2.8.5` | Minor | **Upgrade** |
| `gwt-material.version` | `com.github.gwtmaterialdesign:gwt-material-table` | `2.6.1` | `2.8.5` | Minor | **Upgrade** |
| `gwt-material.version` | `com.github.gwtmaterialdesign:gwt-material-jquery` | `2.6.1` | `2.8.5` | Minor | **Upgrade** |
| `gwt-dominoui.version` | `org.dominokit:domino-ui` | `1.0.0-RC13` | `2.1.0` | Major | **Upgrade** (breaking) |
| `dncomponents.version` | `com.dncomponents.core:*` | `2.4.2` | `3.0.0-alpha-3` | Major (alpha) | **Skip** -- alpha not stable |
| `vue-gwt.version` | `com.axellience:vue-gwt` | `1.0.1` | `1.0.1` | None | No change |

### Libraries and Frameworks

| Property | GroupId:ArtifactId | Current | Latest | Delta | Action |
|---|---|---|---|---|---|
| `gwt-dagger2.version` | `com.google.dagger:dagger-gwt` | `2.43.2` | `2.59.2` | Minor | **Investigate** (dagger-gwt may be removed) |
| `gwt-dagger2.version` | `com.google.dagger:dagger-compiler` | `2.43.2` | `2.59.2` | Minor | **Upgrade** (if dagger-gwt exists) |
| `gwt-restygwt.version` | `org.fusesource.restygwt:restygwt` | `2.2.7` | `2.2.7` | None | No change |
| `rs-api.version` | `javax.ws.rs:javax.ws.rs-api` | `2.1` | `2.1.1` | Patch | **Upgrade** |
| `gwt-mockito.version` | `com.google.gwt.gwtmockito:gwtmockito` | `1.1.9` | `1.1.9` | None | No change |
| `gwt-eventbinder.version` | `com.google.gwt.eventbinder:eventbinder` | `1.1.0` | `1.1.0` | None | No change |
| `gwt-gin.version` | `io.github.gwtplus.gin:gin` | `3.0.0` | `3.0.0` | None | No change |
| `gwt-elemento.version` | `org.jboss.elemento:elemento-core` | `1.0.10` | `2.4.9` | Major | **Upgrade** (breaking) |
| `gwt-domino-rest.version` | `org.dominokit:domino-rest-client` | `1.0.0-RC7` | `2.0.0` | Major | **Upgrade** (breaking) |
| `gwt-domino-rest.version` | `org.dominokit:domino-rest-processor` | `1.0.0-RC7` | `2.0.0` | Major | **Upgrade** (breaking) |
| `gwt-domino-rest.version` | `org.dominokit:domino-rest-shared` | `1.0.0-RC7` | `2.0.0` | Major | **Upgrade** (breaking) |
| `rx-gwt.version` | `com.intendia.gwt.rxgwt2:rxgwt` | `2.3` | `2.3` | None | No change |
| `rx-java-gwt.version` | `com.intendia.gwt:rxjava2-gwt` | `2.2.20-gwt1` | `2.2.20-gwt1` | None | No change |
| `inject-api.version` | `javax.inject:javax.inject` | `1` | `1` | None | No change |

### Build Plugins

| Property | GroupId:ArtifactId | Current | Latest | Action |
|---|---|---|---|---|
| `gwt-maven-plugin.version` | `net.ltgt.gwt.maven:gwt-maven-plugin` | `1.0.1` | Verify | **Check** |
| -- | `org.apache.maven.plugins:maven-compiler-plugin` | `3.7.0` | `3.13.0` | **Upgrade** |

---

## Transitive Dependencies with Updates Available

These are pulled in transitively by the GWT BOM or by third-party libraries.
They are NOT directly managed in `gwt-boot-dependencies/pom.xml` and should
generally NOT be added there unless needed to resolve conflicts.

| GroupId:ArtifactId | Current | Latest | Notes |
|---|---|---|---|
| `org.ow2.asm:asm` | `9.2` | `9.9.1` | Via GWT |
| `org.ow2.asm:asm-commons` | `9.2` | `9.9.1` | Via GWT |
| `org.ow2.asm:asm-util` | `9.2` | `9.9.1` | Via GWT |
| `com.google.code.findbugs:jsr305` | `1.3.9` | `3.0.2` | Via GWT |
| `com.google.code.gson:gson` | `2.6.2` | `2.13.2` | Via GWT |
| `com.google.jsinterop:jsinterop-annotations` | `2.0.0` | `2.1.0` | Via GWT |
| `com.ibm.icu:icu4j` | `63.1` | `78.3` | Via GWT |
| `commons-io:commons-io` | `2.4` | `2.21.0` | Via GWT |
| `net.sourceforge.htmlunit:htmlunit` | `2.19` | `2.70.0` | Via GWT (test) |
| `org.eclipse.jetty:*` | `9.4.44.v20210927` | `12.1.7` | Via GWT (dev mode) |
| `javax.servlet:javax.servlet-api` | `3.1.0` | `4.0.1` | Via GWT |
| `javax.validation:validation-api` | `1.0.0.GA` | `2.0.1.Final` | Via GWT |

**Note:** Most transitive dependency updates will be resolved automatically
when upgrading GWT to 2.13.0, as the GWT BOM will pull in its own updated
transitives.

---

## Summary

| Category | Upgradeable | No Change | Skip (unstable) | Total |
|---|---|---|---|---|
| Core GWT | 1 (affects 4+ artifacts) | 0 | 0 | 1 |
| UI Frameworks | 3 | 1 | 1 | 5 |
| Libraries | 4 | 6 | 0 | 10 |
| Build Plugins | 2 | 0 | 0 | 2 |
| **Total** | **10** | **7** | **1** | **18** |

### Dependencies with Breaking Changes Expected
1. **DominoUI** `1.0.0-RC13` -> `2.1.0` (major rewrite)
2. **Elemento** `1.0.10` -> `2.4.9` (major rewrite)
3. **Domino REST** `1.0.0-RC7` -> `2.0.0` (major release)
4. **GWTBootstrap3** `0.9.4` -> `1.0.1` (major version)
5. **Dagger** `2.43.2` -> `2.59.2` (GWT support uncertain)
