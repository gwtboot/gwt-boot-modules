# GWT Boot: Starters

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

| Name | Framework | Supported Browser Technology |
| ------------- | ------------- |:-------------:| 
| gwt-boot-starter-parent | Parent starter for GWT Boot | No web | 
| gwt-boot-starter | Standard GWT widgets | Widget | 
| gwt-boot-starter-ui-domino | [domino-ui](https://github.com/vegegoku/domino-ui) | Elemental2 | 
| gwt-boot-starter-ui-gwtbootstrap3 | [gwtbootstrap3](https://github.com/gwtbootstrap3/gwtbootstrap3) | Widget | 
| gwt-boot-starter-ui-vuegwt | [vue-gwt](https://github.com/Axellience/vue-gwt) | Elemental2 | 
| gwt-boot-starter-ui-gwtmaterial | [gwt-material](https://github.com/GwtMaterialDesign/gwt-material) | Widget | 
| gwt-boot-starter-ui-errai | [errai](https://github.com/errai/errai) | Elemental2 | 
| gwt-boot-starter-rxgwt | [rxgwt](https://github.com/intendia-oss/rxgwt) | No web | 
| gwt-boot-starter-restygwt | [resty-gwt](https://github.com/resty-gwt/resty-gwt) | No web | 
| gwt-boot-starter-test | [gwtmockito](https://github.com/google/gwtmockito) | No web | 
| gwt-boot-starter-gwteventbinder | [gwteventbinder](https://github.com/google/gwteventbinder) | No web | 
| gwt-boot-starter-gin | [gin](https://github.com/nishtahir/google-gin) | No web | 
| gwt-boot-starter-with-spring-boot | Standard GWT running with [Spring Boot](https://github.com/spring-projects/spring-boot) | Widget | 

## Using GWT Boot Starters

### Using gwt-boot-starter-parent as Parent POM

Similar to [Spring Boot with Parent POM](http://www.baeldung.com/spring-boot-start)

### Using without Parent POM

Similar to [Spring Boot without Parent POM](http://www.baeldung.com/spring-boot-dependency-management-custom-parent)