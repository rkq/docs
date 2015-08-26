# Java Platform

## 1. Language Feature

### 1.1 Exception Handling

##### Types of Exceptions

![exception hierarchy](https://github.com/rkq/docs/blob/master/pics/java_platform_exception_hierarchy.png)

**Checked exceptions** are exceptions that must be declared in the throws clause of a method. They extend Exception and are intended to be an “in your face” type of exceptions. Java wants you to handle them because they somehow are dependent on external factors outside your program. *A checked exception indicates an expected problem that can occur during normal system operation. Mostly these exception happen when you try to use external systems over network or in file system.* Mostly, the correct response to a checked exception should be to try again later, or to prompt the user to modify his input.

**Unchecked exceptions** are exceptions that do not need to be declared in a throws clause. *JVM simply doesn’t force you to handle them as they are mostly generated at runtime due to programmatic errors.* They extend RuntimeException. The most common example is a NullPointerException [Quite scary.. Isn’t it?]. An unchecked exception probably shouldn’t be retried, and the correct action should be usually to do nothing, and let it come out of your method and through the execution stack. At a high level of execution, this type of exceptions should be logged.

**Errors** are serious runtime environment problems that are almost certainly not recoverable. Some examples are OutOfMemoryError, LinkageError, and StackOverflowError. They generally crash you program or part of program. Only a good logging practice will help you in determining the exact causes of errors.

#### User Defined Exceptions

Anytime when user feels that he wants to use its own application specific exception for some reasons, he can create a new class extending appropriate super class (mostly its Exception.java) and start using it in appropriate places. These user defined exceptions can be used in two ways:

1) Either directly throw the custom exception when something goes wrong in application

```
throw new DaoObjectNotFoundException("Couldn't find dao with id " + id);
```


2) Or wrap the original exception inside custom exception and throw it

```
catch (NoSuchMethodException e) {
  throw new DaoObjectNotFoundException("Couldn't find dao with id " + id, e);
}
```
*Wrapping an exception can provide extra information to the user by adding your own message/ context information, while still preserving the stack trace and message of the original exception. It also allows you to hide the implementation details of your code, which is the most important reason to wrap exceptions.*

#### Best Practice

### 1.2 Generics

## 2. Frameworks & Libraries

### 2.1 Spring
### 2.2 Netty
### 2.3 Generic APIs

* Java Platform API <http://docs.oracle.com/javase/8/docs/api/>
* Google Guava <http://code.google.com/p/guava-libraries/>
* Apache Commons <http://commons.apache.org>

### 2.4 Command Line Parsing

* Jewel CLI <http://jewelcli.lexicalscope.com>

### 2.5 Logging, Metrics and Eventing

* Simple Logging Facade for Java (SLF4J) <http://www.slf4j.org>
* Log4j 1 <http://logging.apache.org/log4j/1.2/>
* Log4j 1 extras <http://logging.apache.org/log4j/extras/>
* Log4j 2 <http://logging.apache.org/log4j/2.x/>
* Logback <http://logback.qos.ch>

* Metrics provides a powerful toolkit of ways to measure the behavior of critical components in your production environment. <http://metrics.dropwizard.io>

* Dropwizard has out-of-the-box support for sophisticated configuration, application metrics, logging, operational tools, and much more, allowing you and your team to ship a production-quality web service in the shortest time possible. <http://www.dropwizard.io>

### 2.6 Unit Testing & Mocking

* JUnit <http://junit.org>
* TestNG <http://testng.org>
* jMock <http://www.jmock.org>
* EasyMock <http://easymock.org>
* Mockito <http://mockito.org>

### 2.7 JSON

* Jackson <http://wiki.fasterxml.com/JacksonHome>
* json-schema <http://json-schema.org>

### 2.8 Http Clients

* HttpComponents <http://hc.apache.org>
* Google Http Client <https://github.com/google/google-http-java-client>
* OkHttp <http://square.github.io/okhttp/>


## 3. Java Virtual Machine
### 3.1 Memory Management

## 4. Middlewares
### 4.1 Tomcat
### 4.2 Jetty

## 5. Toolset
### 5.1 Continuous Delivery
#### 5.1.1 Maven
#### 5.1.2 Jenkins
### 5.2 JDK Tools
