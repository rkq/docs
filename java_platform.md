# Java Platform

The Java platform consists of three parts:

1. Java programming language;
2. Java API, frameworks, libraries, middlewares and toolset;
3. Java virtual machine.

## 1. Language Feature

<https://docs.oracle.com/javase/tutorial/>

### Enssential Classes to Understand Java

#### Class java.lang.Object

Class Object is the root of the class hierarchy. Every class has Object as a superclass. All objects, including arrays, implement the methods of this class.

<http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html>

#### Class java.lang.Class<T>

Instances of the class Class represent classes and interfaces in a running Java application. An enum is a kind of class and an annotation is a kind of interface. Every array also belongs to a class that is reflected as a Class object that is shared by all arrays with the same element type and number of dimensions. The primitive Java types (boolean, byte, char, short, int, long, float, and double), and the keyword void are also represented as Class objects.

<http://docs.oracle.com/javase/8/docs/api/java/lang/Class.html>

#### Class java.lang.ClassLoader

A class loader is an object that is responsible for loading classes. The class ClassLoader is an abstract class. Given the binary name of a class, a class loader should attempt to locate or generate data that constitutes a definition for the class. A typical strategy is to transform the name into a file name and then read a "class file" of that name from a file system.

<http://docs.oracle.com/javase/8/docs/api/java/lang/ClassLoader.html>

### Annotations

<https://docs.oracle.com/javase/tutorial/java/annotations/index.html>

Annotations, a form of metadata, provide data about a program that is not part of the program itself. Annotations have no direct effect on the operation of the code they annotate.

Annotations have a number of uses, among them:

* Information for the compiler — Annotations can be used by the compiler to detect errors or suppress warnings.
* Compile-time and deployment-time processing — Software tools can process annotation information to generate code, XML files, and so forth.
* Runtime processing — Some annotations are available to be examined at runtime.

Annotations can be applied to declarations: declarations of classes, fields, methods, and other program elements. When used on a declaration, each annotation often appears, by convention, on its own line. As of the Java SE 8 release, annotations can also be applied to the use of types.


**Predefined Annotation Types**

<https://docs.oracle.com/javase/tutorial/java/annotations/predefined.html>

### Reflection


### Generics

### Exception Handling

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

**Use exceptions only for exceptional conditions**

A well-designed API must not force its clients to use exceptions for ordinary control flow. 

**Use checked exceptions for recoverable conditions and runtime exceptions for programming errors**

Use checked exceptions for conditions from which the caller can reasonably be expected to recover. By throwing a checked exception, you force the caller to handle the exception in a catch clause or to propagate it out-ward.

Use runtime exceptions to indicate programming errors. The great major-ity of runtime exceptions indicate precondition violations. A precondition viola- tion is simply a failure by the client of an API to adhere to the contract established by the API specification.

While the Java Language Specification does not require it, there is a strong convention that errors are reserved for use by the JVM to indicate resource defi- ciencies, invariant failures, or other conditions that make it impossible to continue execution. Given the almost universal acceptance of this convention, it’s best not to implement any new Error subclasses. Therefore, all of the unchecked throw- ables you implement should subclass RuntimeException (directly or indi- rectly).

API designers often forget that exceptions are full-fledged objects on which arbitrary methods can be defined. The primary use of such methods is to provide the code that catches the exception with additional information concerning the condition that caused the exception to be thrown. Because checked exceptions generally indicate recoverable conditions, it’s especially important for such exceptions to provide methods that furnish informa- tion that could help the caller to recover. For example, suppose a checked excep- tion is thrown when an attempt to make a purchase with a gift card fails because the card doesn’t have enough money left on it. The exception should provide an accessor method to query the amount of the shortfall, so the amount can be relayed to the shopper.

**Avoid unnecessary use of checked exceptions**

Checked exceptions are a wonderful feature of the Java programming language. Unlike return codes, they force the programmer to deal with exceptional conditions, greatly enhancing reliability. That said, overuse of checked exceptions can make an API far less pleasant to use. If a method throws one or more checked exceptions, the code that invokes the method must handle the exceptions in one or more catch blocks, or it must declare that it throws the exceptions and let them propagate out- ward. Either way, it places a nontrivial burden on the programmer.
The burden is justified if the exceptional condition cannot be prevented by proper use of the API and the programmer using the API can take some useful action once confronted with the exception. Unless both of these conditions hold, an unchecked exception is more appropriate. As a litmus test, ask yourself how the programmer will handle the exception. Is this the best that can be done? If the programmer using the API can do no better, an unchecked exception would be more appropriate.One technique for turning a checked exception into an unchecked exception is to break the method that throws the exception into two methods, the first of which returns a boolean that indicates whether the exception would be thrown.
**Favor the use of standard exceptions**
Reusing preexisting exceptions has several benefits. Chief among these, it makes your API easier to learn and use because it matches established conven- tions with which programmers are already familiar. A close second is that pro- grams using your API are easier to read because they aren’t cluttered with unfamiliar exceptions. Last (and least), fewer exception classes mean a smaller memory footprint and less time spent loading classes.**Throw exceptions appropriate to the abstraction**
Higher layers should catch lower-level exceptions and, in their place, throw exceptions that can be explained in terms of the higher-level abstraction. This idiom is known as exception translation.A special form of exception translation called exception chaining is appropri- ate in cases where the lower-level exception might be helpful to someone debug- ging the problem that caused the higher-level exception. The lower-level exception (the cause) is passed to the higher-level exception, which provides anaccessor method (Throwable.getCause) to retrieve the lower-level exception.
While exception translation is superior to mindless propagation of excep- tions from lower layers, it should not be overused. Where possible, the best way to deal with exceptions from lower layers is to avoid them, by ensuring that lower-level methods succeed. Sometimes you can do this by checking the validity of the higher-level method’s parameters before passing them on to lower layers.
If it is impossible to prevent exceptions from lower layers, the next best thing is to have the higher layer silently work around these exceptions, insulating the caller of the higher-level method from lower-level problems. Under these circum- stances, it may be appropriate to log the exception using some appropriate logging facility such as java.util.logging. This allows an administrator to investigate the problem, while insulating the client code and the end user from it.

**Constructor throws exception**

Release acquired resources during the object constructing.


### Nested Classes

### Common Programming Practice

**Secure Coding Guidelines for Java SE**

<http://www.oracle.com/technetwork/java/seccodeguide-139067.html>

**“State-dependent” Method**

A class with a “state-dependent” method that can be invoked only under certain unpredict-able conditions should generally have a separate “state-testing” method indicating whether it is appropriate to invoke the state-dependent method. For example, the Iterator interface has the state-dependent method next and the corresponding state-testing method hasNext. An alternative to providing a separate state-testing method is to have the state-dependent method return a distinguished value such as null if it is invoked with the object in an inappropriate state.

Here are some guidelines to help you choose between a state-testing method and a distinguished return value. If an object is to be accessed concurrently without external synchronization or is subject to externally induced state transitions, you must use a distinguished return value, as the object’s state could change in the interval between the invocation of a state-testing method and its state-dependent method. Performance concerns may dictate that a distinguished return value be used if a separate state-testing method would duplicate the work of the state- dependent method. All other things being equal, a state-testing method is mildly preferable to a distinguished return value. It offers slightly better readability, and incorrect use may be easier to detect: if you forget to call a state-testing method, the state-dependent method will throw an *unchecked* exception, making the bug obvious; if you forget to check for a distinguished return value, the bug may be subtle.


## 2. APIs, Frameworks and Libraries

### Spring

<http://spring.io>

#### The IoC Container

**Classpath Scanning**

### Netty

<http://netty.io>

### Generic APIs

* Java Platform API <http://docs.oracle.com/javase/8/docs/api/>
* Google Guava <http://code.google.com/p/guava-libraries/>
* Apache Commons <http://commons.apache.org>

### Command Line Parsing

* Jewel CLI <http://jewelcli.lexicalscope.com>

### Logging, Metrics and Eventing

* Simple Logging Facade for Java (SLF4J) <http://www.slf4j.org>
* Log4j 1 <http://logging.apache.org/log4j/1.2/>
* Log4j 1 extras <http://logging.apache.org/log4j/extras/>
* Log4j 2 <http://logging.apache.org/log4j/2.x/>
* Logback <http://logback.qos.ch>

* Metrics provides a powerful toolkit of ways to measure the behavior of critical components in your production environment. <http://metrics.dropwizard.io>

* Dropwizard has out-of-the-box support for sophisticated configuration, application metrics, logging, operational tools, and much more, allowing you and your team to ship a production-quality web service in the shortest time possible. <http://www.dropwizard.io>

### Unit Testing & Mocking

* JUnit <http://junit.org>
* TestNG <http://testng.org>
* jMock <http://www.jmock.org>
* EasyMock <http://easymock.org>
* Mockito <http://mockito.org>

### JSON

* Jackson <http://wiki.fasterxml.com/JacksonHome>
* json-schema <http://json-schema.org>

### Http Clients

* HttpComponents <http://hc.apache.org>
* Google Http Client <https://github.com/google/google-http-java-client>
* OkHttp <http://square.github.io/okhttp/>


### Java Servlet Technology




## 3. Middlewares

### Tomcat

<http://tomcat.apache.org>

### Jetty

<http://www.eclipse.org/jetty/>

## 4. Toolset
### Continuous Delivery
#### Maven

<http://maven.apache.org>

<http://mvnrepository.com>

#### Jenkins

<http://jenkins-ci.org>

#### TeamCity

<https://www.jetbrains.com/teamcity/>

### JDK Tools

## 5. Java Virtual Machine
### Garbage Collector

### JIT Compiler

### VM Runtime

