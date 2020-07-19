# GWT Boot: Starters

[![Build Status](https://travis-ci.org/gwtboot/gwt-boot-modules.svg?branch=master)](https://travis-ci.org/gwtboot/gwt-boot-modules)

## GWT BOMs and POMs - GWT Dependencies and Starters

!!!GWT Boot Starter is !NOT! an integration between Spring Boot and GWT!!!

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
spring-boot-starter-ui-domino dependency in your project, 
and you are good to go.

## List of all supported GWT frameworks

| Name                               | Framework                                                         | Supported Browser Technology | Status     | Examples                                                                                                                                                                                                                                         |
| ---------------------------------- | ----------------------------------------------------------------- | ---------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gwt-boot-starter-parent            | Parent starter for GWT Boot                                       | No web                       | Integrated | -                                                                                                                                                                                                                                                |
| gwt-boot-starter                   | Standard GWT widgets                                              | Widget                       | Integrated | [gwt-boot-sample-basic](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-basic)                                                                                                                                           |
| gwt-boot-starter-ui-domino         | [domino-ui](https://github.com/DominoKit/domino-ui)               | Elemental2                   | Integrated | [gwt-boot-sample-ui-domino](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino), [gwt-boot-sample-ui-domino-dagger2](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino-dagger2)   |
| gwt-boot-starter-ui-gwtbootstrap3  | [gwtbootstrap3](https://github.com/gwtbootstrap3/gwtbootstrap3)   | Widget                       | Integrated | [gwt-boot-sample-ui-gwtbootstrap3](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-gwtbootstrap3)                                                                                                                     |
| gwt-boot-starter-ui-vue-gwt        | [vue-gwt](https://github.com/Axellience/vue-gwt)                  | Elemental2                   | Integrated | [gwt-boot-sample-ui-vue-gwt](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-vue-gwt)                                                                                                                                 |
| gwt-boot-starter-ui-gwtreact       | [gwt-react](https://github.com/GWTReact/gwt-react)                | Elemental2                   | -          | -                                                                                                                                                                                                                                                |
| gwt-boot-starter-ui-gwtmaterial    | [gwt-material](https://github.com/GwtMaterialDesign/gwt-material) | Widget                       | Integrated | [gwt-boot-sample-ui-gwtmaterial](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-gwtmaterial)                                                                                                                         |
| gwt-boot-starter-ui-errai          | [errai](https://github.com/errai/errai)                           | Elemental2                   | -          | -                                                                                                                                                                                                                                                |
| gwt-boot-starter-rxgwt             | [rxgwt](https://github.com/intendia-oss/rxgwt)                    | No web                       | Integrated | [gwt-boot-sample-rxgwt](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-rxgwt)                                                                                                                                           |  |
| gwt-boot-starter-restygwt          | [resty-gwt](https://github.com/resty-gwt/resty-gwt)               | No web                       | Integrated | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection)                                                                                                                                 |
| gwt-boot-starter-test              | [gwtmockito](https://github.com/google/gwtmockito)                | No web                       | Integrated | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection), [gwt-boot-sample-ui-domino-dagger2](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino-dagger2) |
| gwt-boot-starter-gwteventbinder    | [gwteventbinder](https://github.com/google/gwteventbinder)        | No web                       | Integrated | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection)                                                                                                                                 |
| gwt-boot-starter-gin               | [gin](https://github.com/gwtplus/google-gin)                      | No web                       | Integrated | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection)                                                                                                                                 |
| gwt-boot-starter-dagger2           | [dagger2](https://google.github.io/dagger)                        | No web                       | Integrated | [gwt-boot-sample-ui-domino-dagger2](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-domino-dagger2)                                                                                                                   |
| gwt-boot-starter-elemento-core     | [elemento](https://github.com/hal/elemento)                       | Elemental2                   | Integrated | [gwt-boot-sample-elemento-core](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-elemento-core)                                                                                                                           |
| gwt-boot-starter-elemento-template | [elemento](https://github.com/hal/elemento)                       | Elemental2                   | Integrated | [gwt-boot-sample-elemento-template](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-elemento-template)                                                                                                                   |
| gwt-boot-starter-domino-rest       | [domino-rest](https://github.com/DominoKit/domino-rest)           | Elemental2                   | Integrated | [gwt-boot-sample-domino-rest](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-domino-rest)                                                                                                                               |

## Using GWT Boot Starters

### Using gwt-boot-starter-parent as Parent POM

Similar to [Spring Boot with Parent POM](http://www.baeldung.com/spring-boot-start)

### Using without Parent POM

Similar to [Spring Boot without Parent POM](http://www.baeldung.com/spring-boot-dependency-management-custom-parent)

## Wiki

Check out our Wiki for [How-Tos](https://github.com/gwtboot/gwt-boot-modules/wiki) and other information.

## Examples

Example of each Starter can be found at the table above "Examples" column. All the examples are in this [repository](https://github.com/gwtboot/gwt-boot-samples).
