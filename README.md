# GWT Boot: Starters

[![Build Status](https://travis-ci.org/gwtboot/gwt-boot-modules.svg?branch=master)](https://travis-ci.org/gwtboot/gwt-boot-modules)

## GWT BOMs and POMs - GWT Dependencies and Starters

GWT Boot Starter dependencies is basically a simple Starter dependencies 
collection for GWT just like Spring Boot Starter dependencies.
The idea is taken from 
[Spring Boot Starters](https://github.com/spring-projects/spring-boot/tree/master/spring-boot-project/spring-boot-starters)

GWT Boot Starters are a set of convenient dependency descriptors 
that you can include in your application. 
You get a one-stop-shop for all the GWT and related technology 
that you need without having to hunt through sample code and 
copy paste loads of dependency descriptors. For example, 
if you want to get started using GWT and [Domino UI](https://github.com/vegegoku/domino-ui) 
for your Material Design and [Elemental2](https://github.com/google/elemental2) just include the 
spring-boot-starter-ui-domino dependency in your project, 
and you are good to go.

## List of all supported GWT frameworks

| Name | Framework | Supported Browser Technology | Status | Examples |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| gwt-boot-starter-parent | Parent starter for GWT Boot | No web | Integrated | - |
| gwt-boot-starter | Standard GWT widgets | Widget | Integrated | [gwt-boot-sample-basic](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-basic) |
| gwt-boot-starter-ui-domino | [domino-ui](https://github.com/vegegoku/domino-ui) | Elemental2 | - | - |
| gwt-boot-starter-ui-gwtbootstrap3 | [gwtbootstrap3](https://github.com/gwtbootstrap3/gwtbootstrap3) | Widget | Integrated | [gwt-boot-sample-ui-gwtbootstrap3][https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-gwtbootstrap3] |
| gwt-boot-starter-ui-vuegwt | [vue-gwt](https://github.com/Axellience/vue-gwt) | Elemental2 | - | - |
| gwt-boot-starter-ui-gwtmaterial | [gwt-material](https://github.com/GwtMaterialDesign/gwt-material) | Widget | In Process | [gwt-boot-sample-ui-gwtmaterial](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-ui-gwtmaterial) |
| gwt-boot-starter-ui-errai | [errai](https://github.com/errai/errai) | Elemental2 | - | - |
| gwt-boot-starter-rxgwt | [rxgwt](https://github.com/intendia-oss/rxgwt) | No web | - | - |
| gwt-boot-starter-restygwt | [resty-gwt](https://github.com/resty-gwt/resty-gwt) | No web | In Process | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection) |
| gwt-boot-starter-test | [gwtmockito](https://github.com/google/gwtmockito) | No web | In Process | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection) |
| gwt-boot-starter-gwteventbinder | [gwteventbinder](https://github.com/google/gwteventbinder) | No web | In Process | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection) |
| gwt-boot-starter-gin | [gin](https://github.com/nishtahir/google-gin) | No web | Integrated | [gwt-boot-sample-collection](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-collection) |

For Spring Boot developers there are separate starters with **"*-with-spring-boot"**.

| Name | Framework | Supported Browser Technology | Status | Examples |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| gwt-boot-starter-parent-with-spring-boot | Parent starter for GWT Boot with [Spring Boot](https://github.com/spring-projects/spring-boot) | No web | Integrated | - |
| gwt-boot-starter-with-spring-boot | Standard GWT running with [Spring Boot](https://github.com/spring-projects/spring-boot) | Widget | Integrated | [gwt-boot-sample-basic-with-spring-boot](https://github.com/gwtboot/gwt-boot-samples/tree/master/gwt-boot-sample-basic-with-spring-boot) |

## Using GWT Boot Starters

### Using gwt-boot-starter-parent as Parent POM

Similar to [Spring Boot with Parent POM](http://www.baeldung.com/spring-boot-start)

### Using without Parent POM

Similar to [Spring Boot without Parent POM](http://www.baeldung.com/spring-boot-dependency-management-custom-parent)