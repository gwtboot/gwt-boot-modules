# GWT Boot: Starters

![Build Status](https://github.com/gwtboot/gwt-boot-modules/actions/workflows/maven.yml/badge.svg)

## GWT BOMs and POMs - GWT Dependencies and Starters

**GWT Boot Starter is NOT an integration between Spring Boot and GWT!**

If you need a modern introduction to GWT / J2CL take a look at this [Padlet for GWT / J2CL](https://bit.ly/GWTIntroPadlet).

GWT Boot Starter dependencies is basically a simple Starter dependencies 
collection for GWT just like Spring Boot Starter dependencies.
The idea is taken from 
[Spring Boot Starters](https://github.com/spring-projects/spring-boot/tree/master/spring-boot-project/spring-boot-starters)

GWT Boot Starters are a set of convenient dependency descriptors 
that you can include in your application. 
You get a one-stop-shop for all the GWT and related technology 
that you need without having to hunt through sample code and 
copy paste loads of dependency descriptors. For example, 
if you want to get started using GWT and [Domino UI](https://github.com/DominoKit/domino-ui) 
for your Material Design and [Elemental2](https://github.com/google/elemental2) just include the 
`gwt-boot-starter-ui-domino` dependency in your project, 
and you are good to go.

**GWT Boot Starter artifacts are released on the [Maven Central](https://search.maven.org/search?q=com.github.gwtboot)**

## List of all supported GWT frameworks

| ArtifactId / GWT Module: com.github.gwtboot.starter.*                              | Framework                                                         | Supported Browser Technology | Status     | GWT / Elemento Core Version | Examples                                                                                                                                                                                                                                         |
| ---------------------------------- | ----------------------------------------------------------------- | ---------------------------- | ---------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gwt-boot-starter-parent            | Parent starter for GWT Boot                                       | No web                       | Integrated | -                           | -                                                                                                                                                                                                                                                |
| gwt-boot-starter / Starter                  | Standard GWT widgets                                              | Widget                       | Integrated | 2.10.0                       | [gwt-boot-sample-basic](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-basic)                                                                                                                                           |
| gwt-boot-starter-ui-domino / DominoStarter        | [domino-ui](https://github.com/DominoKit/domino-ui)               | Elemental2                   | Integrated | 2.10.0              | [gwt-boot-sample-ui-domino](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino), [gwt-boot-sample-ui-domino-dagger2](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino-dagger2)   |
| gwt-boot-starter-ui-gwtbootstrap3 / GwtBootstrap3Starter | [gwtbootstrap3](https://github.com/gwtbootstrap3/gwtbootstrap3)   | Widget                       | Integrated | 2.10.0                       | [gwt-boot-sample-ui-gwtbootstrap3](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-gwtbootstrap3)                                                                                                                     |
| gwt-boot-starter-ui-vue-gwt / VueGwtStarter        | [vue-gwt](https://github.com/Axellience/vue-gwt)                  | Elemental2                   | Integrated | 2.10.0                       | [gwt-boot-sample-ui-vue-gwt](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-vue-gwt)                                                                                                                                 |
| gwt-boot-starter-ui-gwtreact       | [gwt-react](https://github.com/GWTReact/gwt-react)                | Elemental2                   | -          |                             | -                                                                                                                                                                                                                                                |
| gwt-boot-starter-ui-gwtmaterial / GwtMaterialStarter   | [gwt-material](https://github.com/GwtMaterialDesign/gwt-material) | Widget                       | Integrated | 2.10.0                       | [gwt-boot-sample-ui-gwtmaterial](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-gwtmaterial)                                                                                                                         |
| gwt-boot-starter-ui-errai          | [errai](https://github.com/errai/errai)                           | Elemental2                   | -          | -                           | -                                                                                                                                                                                                                                                |
| gwt-boot-starter-rxgwt / RxGwtStarter             | [rxgwt](https://github.com/intendia-oss/rxgwt)                    | No web                       | Integrated | 2.10.0      | [gwt-boot-sample-rxgwt](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-rxgwt)                                                                                                                                           |  
| gwt-boot-starter-restygwt / RestyGwtStarter         | [resty-gwt](https://github.com/resty-gwt/resty-gwt)               | No web                       | Integrated | 2.10.0                       | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection)                                                                                                                                 |
| gwt-boot-starter-test              | [gwtmockito](https://github.com/google/gwtmockito)                | No web                       | Integrated | 2.10.0                       | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection), [gwt-boot-sample-ui-domino-dagger2](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino-dagger2) |
| gwt-boot-starter-gwteventbinder / GwtEventBinderStarter    | [gwteventbinder](https://github.com/google/gwteventbinder)        | No web                       | Integrated | 2.10.0                       | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection)                                                                                                                                 |
| gwt-boot-starter-gin / GinStarter              | [gin](https://github.com/gwtplus/google-gin)                      | No web                       | Integrated | 2.10.0                       | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection)                                                                                                                                 |
| gwt-boot-starter-dagger2 / Dagger2Starter          | [dagger2](https://google.github.io/dagger)                        | No web                       | Integrated | 2.10.0                       | [gwt-boot-sample-ui-domino-dagger2](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino-dagger2)                                                                                                                   |
| gwt-boot-starter-elemento-core / ElementoCoreStarter    | [elemento](https://github.com/hal/elemento)                       | Elemental2                   | Integrated | 2.10.0               | [gwt-boot-sample-elemento-core](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-elemento-core)                                                                                                                           |
| gwt-boot-starter-domino-rest / DominoRestStarter      | [domino-rest](https://github.com/DominoKit/domino-rest)           | Elemental2                   | Integrated | 2.10.0                       | [gwt-boot-sample-domino-rest](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-domino-rest)                                                                                                                               |
| gwt-boot-starter-nalu              | [nalu](https://github.com/NaluKit/nalu)                           | No web                       | -          | -                           | -                                                                                                                                                                                                                                                |
| gwt-boot-starter-dncomponents / DncomponentsStarter     | [dn-components](https://dncomponents.com)                         | Elemental2                   | Integrated | 2.10.0                       | [gwt-boot-sample-ui-dncomponents](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-dncomponents)                                                                                                                                                                                                                                                |

## Using GWT Boot Starters

### Using gwt-boot-starter-parent as Parent POM

Similar to [Spring Boot with Parent POM](http://www.baeldung.com/spring-boot-start)

### Using without Parent POM

Similar to [Spring Boot without Parent POM](http://www.baeldung.com/spring-boot-dependency-management-custom-parent)

## Wiki

Check out our Wiki for [How-Tos](https://github.com/gwtboot/gwt-boot-modules/wiki) and other information.

## Examples

Example of each Starter can be found at the table above "Examples" column. All the examples are in this [repository](https://github.com/gwtboot/gwt-boot-samples).
