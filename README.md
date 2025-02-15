# Struts7-Thymeleaf3-plugin

[![Maven Package](https://github.com/A-pZ/struts7-thymeleaf3-plugin/actions/workflows/maven-publish.yml/badge.svg)](https://github.com/A-pZ/struts7-thymeleaf3-plugin/actions/workflows/maven-publish.yml)

This project is Struts2(Version7.0.0)-plugin for use [Thymeleaf](http://www.thymeleaf.org) templating engine version 3.1.3-RELEASE.

This project fork from [Struts2-thymeleaf-plugin](https://github.com/codework/struts2-thymeleaf-plugin), Steven Benitez.

## Release note and update notice.

Version 7.0.0 : Update Struts 7.0.0 and JDK 17, Thymeleaf 3.1.3
Version 6.0.0 : Update Struts 6.0.0 and JDK 11
Version 1.2.0 : Message Resource Bigfix #29 was resolved and Strus2 Version updated 2.5.17. This plugin version only support Struts2.5.17 or later.

If you use bigfix and Struts2 version before 2.5.16, use @psyuhen forked this plugin version 1.0.5.1( https://github.com/psyuhen/struts2-thymeleaf3-plugin/tree/develop/1.0.5.1 ).

## Example Usage

The examples below show you how to map an action's result to a Thymeleaf
template, as well as how to reference the Struts2 action from within the template.

## Sample and Blank app.

https://github.com/A-pZ/struts7-thymeleaf3-sampleapp/

### Action Mapping

    <action name="home" class="com.example.HelloWorldAction">
        <result name="success" type="thymeleaf">/WEB-INF/templates/hello.html</result>
    </action>

### Action Class

    public class HelloWorldAction extends ActionSupport {
      private String message;

      @Override
      public String execute() throws Exception {
        message = "Hello, this is a Thymeleaf example!";

        return SUCCESS;
      }

      public String getMessage() {
        return message;
      }
    }

### Thymeleaf Template

You can refer to properties on the action using the `${action.property}` syntax.
The following template displays the message property of the action.

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

    <html xmlns="http://www.w3.org/1999/xhtml">

    <head>
        <title>Hello World</title>
        <meta content="text/html; charset=UTF-8" http-equiv="Content-Type"/>
    </head>

    <body>

    <p th:text="${message}">This message is only seen during prototyping.</p>

    </body>

    </html>

## Message Resolution

This plugin will cause Thymeleaf to look in the Struts2 i18n resource bundles to resolve messages.
Since version 1.2.0 resolve message resource problem, Original source is @psyuhen ( https://github.com/psyuhen/struts2-thymeleaf3-plugin/tree/develop/1.0.5.1 )

## Configuration

The following reflects the default settings (struts.xml).
If you changed this values, overwriting your configuration files , struts.xml or struts.properties.

    <constant name="struts.thymeleaf.templateMode" value="HTML5"/>
    <constant name="struts.thymeleaf.encoding" value="UTF-8"/>
    <constant name="struts.thymeleaf.prefix" value="/WEB-INF/templates/"/>
    <constant name="struts.thymeleaf.suffix" value=".html"/>
    <constant name="struts.thymeleaf.cacheable" value="true"/>
    <constant name="struts.thymeleaf.cacheTtlMillis" value="3600000"/>
    <constant name="struts.thymeleaf.templateEngineName" value="default"/>

And parent-package set.

    <package name="your-app-default" abstract="true" extends="struts-thymeleaf">

or Struts2-convention-plugin annotation.

    @ParentPackage("struts-thymeleaf")

## License

    Copyright 2025, 2016 A-pZ ( Koji Azuma )
    Original version is Steven Benitez.(org.codework) 2013.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
