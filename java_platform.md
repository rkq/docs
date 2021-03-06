# Java Platform

The Java platform consists of three parts:

1. Java programming language;
2. Java API, frameworks, libraries, middlewares and toolset;
3. Java virtual machine.

## Language Feature

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

### Classes & Objects

#### Nested Classes

The Java programming language allows you to define a class within another class. Nested classes are divided into two categories: static and non-static. Nested classes that are declared static are called *static nested classes*. Non-static nested classes are called *inner classes*.

A nested class is a member of its enclosing class. *Non-static nested classes (inner classes) have access to other members of the enclosing class, even if they are declared private. Static nested classes do not have access to other members of the enclosing class.* As a member of the OuterClass, a nested class can be declared private, public, protected, or package private. (Recall that outer classes can only be declared public or package private.)

###### Static Nested Classes

As with class methods and variables, a static nested class is associated with its outer class. And like static class methods, a static nested class cannot refer directly to instance variables or methods defined in its enclosing class: it can use them only through an object reference. 

A static nested class interacts with the instance members of its outer class (and other classes) just like any other top-level class. In effect, a static nested class is behaviorally a top-level class that has been nested in another top-level class for packaging convenience. 

##### Inner Classes

As with instance methods and variables, an inner class is associated with an instance of its enclosing class and has direct access to that object's methods and fields. Also, because an inner class is associated with an instance, it cannot define any static members itself.

Objects that are instances of an inner class exist within an instance of the outer class.

There are two special kinds of inner classes: *local classes* and *anonymous classes*.

**Local classes** are classes that are defined in a block, which is a group of zero or more statements between balanced braces. You typically find local classes defined in the body of a method. A local class has access to the members of its enclosing class. In addition, a local class has access to local variables. However, a local class can only access local variables that are declared final. When a local class accesses a local variable or parameter of the enclosing block, it captures that variable or parameter. Local classes are similar to inner classes because they cannot define or declare any static members.

**Anonymous classes** enable you to make your code more concise. They enable you to declare and instantiate a class at the same time. They are like local classes except that they do not have a name. Use them if you need to use a local class only once. While local classes are class declarations, anonymous classes are expressions, which means that you define the class in another expression.

##### Lambda Expressions

One issue with anonymous classes is that if the implementation of your anonymous class is very simple, such as an interface that contains only one method, then the syntax of anonymous classes may seem unwieldy and unclear. In these cases, you're usually trying to pass functionality as an argument to another method, such as what action should be taken when someone clicks a button. Lambda expressions enable you to do this, to treat functionality as method argument, or code as data.

A lambda expression consists of the following:

* A comma-separated list of formal parameters enclosed in parentheses. 
* The arrow token, ->
* A body, which consists of a single expression or a statement block.

Like local and anonymous classes, lambda expressions can capture variables; they have the same access to local variables of the enclosing scope. However, unlike local and anonymous classes, lambda expressions do not have any shadowing issues. Lambda expressions are lexically scoped. This means that they do not inherit any names from a supertype or introduce a new level of scoping. Declarations in a lambda expression are interpreted just as they are in the enclosing environment.


**When to Use Nested Classes, Local Classes, Anonymous Classes, and Lambda Expressions **

* Local class: Use it if you need to create more than one instance of a class, access its constructor, or introduce a new, named type (because, for example, you need to invoke additional methods later).
* Anonymous class: Use it if you need to declare fields or additional methods.
* Lambda expression: Use it if you are encapsulating a single unit of behavior that you want to pass to other code. For example, you would use a lambda expression if you want a certain action performed on each element of a collection, when a process is completed, or when a process encounters an error. Use it if you need a simple instance of a functional interface and none of the preceding criteria apply (for example, you do not need a constructor, a named type, fields, or additional methods).
* Nested class: Use it if your requirements are similar to those of a local class, you want to make the type more widely available, and you don't require access to local variables or method parameters. Use a non-static nested class (or inner class) if you require access to an enclosing instance's non-public fields and methods. Use a static nested class if you don't require this access.

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

In a nutshell, generics enable types (classes and interfaces) to be parameters when defining classes, interfaces and methods. Much like the more familiar formal parameters used in method declarations, type parameters provide a way for you to re-use the same code with different inputs. The difference is that the inputs to formal parameters are values, while the inputs to type parameters are types.

Code that uses generics has many benefits over non-generic code:

* Stronger type checks at compile time. A Java compiler applies strong type checking to generic code and issues errors if the code violates type safety. Fixing compile-time errors is easier than fixing runtime errors, which can be difficult to find.
* Elimination of casts.
* Enabling programmers to implement generic algorithms. By using generics, programmers can implement generic algorithms that work on collections of different types, can be customized, and are type safe and easier to read.

You can subtype a generic class or interface by extending or implementing it. The relationship between the type parameters of one class or interface and the type parameters of another are determined by the extends and implements clauses.

#### Bounded Type Parameters

There may be times when you want to restrict the types that can be used as type arguments in a parameterized type. For example, a method that operates on numbers might only want to accept instances of Number or its subclasses. This is what bounded type parameters are for.

To declare a bounded type parameter, list the type parameter's name, followed by the extends keyword, followed by its upper bound, which in this example is Number. Note that, in this context, extends is used in a general sense to mean either "extends" (as in classes) or "implements" (as in interfaces).

A type variable with multiple bounds is a subtype of all the types listed in the bound. If one of the bounds is a class, it must be specified first. 

#### Wildcards

In generic code, the question mark (?), called the wildcard, represents an unknown type. The wildcard can be used in a variety of situations: as the type of a parameter, field, or local variable; sometimes as a return type (though it is better programming practice to be more specific). The wildcard is never used as a type argument for a generic method invocation, a generic class instance creation, or a supertype.

**Upper Bounded Wildcards**

You can use an upper bounded wildcard to relax the restrictions on a variable. To declare an upper-bounded wildcard, use the wildcard character ('?'), followed by the extends keyword, followed by its upper bound. Note that, in this context, extends is used in a general sense to mean either "extends" (as in classes) or "implements" (as in interfaces).

**Unbounded Wildcards**

The unbounded wildcard type is specified using the wildcard character (?), for example, List<?>. This is called a list of unknown type. There are two scenarios where an unbounded wildcard is a useful approach:

* If you are writing a method that can be implemented using functionality provided in the Object class.
* When the code is using methods in the generic class that don't depend on the type parameter. For example, List.size or List.clear. In fact, Class<?> is so often used because most of the methods in Class<T> do not depend on T.

**Lower Bounded Wildcards**

The Upper Bounded Wildcards section shows that an upper bounded wildcard restricts the unknown type to be a specific type or a subtype of that type and is represented using the extends keyword. In a similar way, a lower bounded wildcard restricts the unknown type to be a specific type or a super type of that type.

A lower bounded wildcard is expressed using the wildcard character ('?'), following by the super keyword, followed by its lower bound: <? super A>.




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



### Concurrency

**What does it mean a thread is interrupted?**

**What will happen when a thread throws an exception and that exception is not catched until by JVM?**

### I/O


### Collections



### Common Programming Practice

**Secure Coding Guidelines for Java SE**

<http://www.oracle.com/technetwork/java/seccodeguide-139067.html>

**“State-dependent” Method**

A class with a “state-dependent” method that can be invoked only under certain unpredict-able conditions should generally have a separate “state-testing” method indicating whether it is appropriate to invoke the state-dependent method. For example, the Iterator interface has the state-dependent method next and the corresponding state-testing method hasNext. An alternative to providing a separate state-testing method is to have the state-dependent method return a distinguished value such as null if it is invoked with the object in an inappropriate state.

Here are some guidelines to help you choose between a state-testing method and a distinguished return value. If an object is to be accessed concurrently without external synchronization or is subject to externally induced state transitions, you must use a distinguished return value, as the object’s state could change in the interval between the invocation of a state-testing method and its state-dependent method. Performance concerns may dictate that a distinguished return value be used if a separate state-testing method would duplicate the work of the state- dependent method. All other things being equal, a state-testing method is mildly preferable to a distinguished return value. It offers slightly better readability, and incorrect use may be easier to detect: if you forget to call a state-testing method, the state-dependent method will throw an *unchecked* exception, making the bug obvious; if you forget to check for a distinguished return value, the bug may be subtle.

**Always make a name for created threads, especical for long running threads**


## APIs & Libraries

### Java SE API

Java Platform API <http://docs.oracle.com/javase/8/docs/api/>

#### Java Collection Framework

#### Concurrency

###### ThreadLocal

### Java Servlet Technology

Key Components Concepts:

* Servlet
* Servlet Container
* Request/Response
* Servlet Context
* Listener
* Session
* Web Application: The servlet container must enforce a one to one correspondence between a Web application and a ServletContext. A ServletContext object provides a servlet with its view of the application.

##### Asynchronous Processing


### Generic APIs

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


## Frameworks - Spring

<http://spring.io>


### Core Technologies

#### The IoC Container

IoC is also known as dependency injection (DI). It is a process whereby objects define their dependencies, that is, the other objects they work with, only through constructor arguments, arguments to a factory method, or properties that are set on the object instance after it is constructed or returned from a factory method. The container then injects those dependencies when it creates the bean. This process is fundamentally the inverse, hence the name Inversion of Control (IoC), of the bean itself controlling the instantiation or location of its dependencies by using direct construction of classes.
The org.springframework.beans and org.springframework.context packages are the basis for Spring Framework’s IoC container.
In Spring, the objects that form the backbone of your application and that are managed by the Spring IoC container are called *beans*. A bean is an object that is instantiated, assembled, and otherwise managed by a Spring IoC container. Otherwise, a bean is simply one of many objects in your application. Beans, and the dependencies among them, are reflected in the configuration metadata used by a container.The interface org.springframework.context.ApplicationContext represents the Spring *IoC container* and is responsible for instantiating, configuring, and assembling the aforementioned beans. The container gets its instructions on what objects to instantiate, configure, and assemble by reading *configuration metadata*. The configuration metadata is represented in *XML, Java annotations, or Java code*. It allows you to express the objects that compose your application and the rich interdependencies between such objects.The following diagram is a high-level view of how Spring works. Your application classes are combined with configuration metadata so that after the ApplicationContext is created and initialized, you have a fully configured and executable system or application.
![IoC](https://github.com/rkq/docs/blob/master/pics/java_platform_spring_ioc.png)

Configuration metadata could be:

* XML-based configuration
* Annotation-based configuration
* Java-based configuration
* Convention-based configuration

**Classpath Scanning**

##### Environment Abstraction
The [Environment](http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/core/env/Environment.html) is an abstraction integrated in the container that models two key aspects of the application environment: *profiles* and *properties*.A *profile* is a named, logical group of bean definitions to be registered with the container only if the given profile is active. Beans may be assigned to a profile whether defined in XML or via annotations. The role of the Environment object with relation to profiles is in determining which profiles (if any) are currently active, and which profiles (if any) should be active by default.
*Properties* play an important role in almost all applications, and may originate from a variety of sources: properties files, JVM system properties, system environment variables, JNDI, servlet context parameters, ad-hoc Properties objects, Maps, and so on. The role of the Environment object with relation to properties is to provide the user with a convenient service interface for configuring property sources and resolving properties from them.
**Bean Definition Profiles**Bean definition profiles is a mechanism in the core container that allows for registration of different beans in different environments. The word environment can mean different things to different users and this feature can help with many use cases, including:
* working against an in-memory data source ind evelopment v.s. looking up that same data source from JNDI when in QA or production
* registering monitoring infrastructure only when deploying an application into a performance environment
* registering customized implementations of beans for customer A v.s.customer B deployments

The @Profile annotation allows you to indicate that a component is eligible for registration when one or more specified profiles are active.

*If a @Configuration class is marked with @Profile, all of the @Bean methods and @Import annotations associated with that class will be bypassed unless one or more of the specified profiles are active.*

Activating a profile can be done in several ways, but the most straightforward is to do it programmatically against the Environment API which is available via an ApplicationContext.

In addition, profiles may also be activated declaratively through the *spring.profiles.active* property which may be specified through system environment variables, JVM system properties, servlet context parameters in web.xml, or even as an entry in JNDI (see the section called “PropertySource abstraction”). In integration tests, active profiles can be declared via the @ActiveProfiles annotation in the spring-test module (see the section called “Context configuration with environment profiles”).

Note that profiles are not an "either-or" proposition; it is possible to activate multiple profiles at once.
*The default profile represents the profile that is enabled by default. If no profile is active, the dataSource above will be created; this can be seen as a way to provide a default definition for one or more beans. If any profile is enabled, the default profile will not apply.* The name of the default profile can be changed using setDefaultProfiles() on the Environment or declaratively using the spring.profiles.default property.**PropertySource Abstraction**Spring’s Environment abstraction provides search operations over a configurable hierarchy of property sources.
A PropertySource is a simple abstraction over any source of key-value pairs, and Spring’s StandardEnvironment is configured with two PropertySource objects — one representing the set of JVM system properties (a la System.getProperties()) and one representing the set of system environment variables (a la System.getenv()).
The Environment object perform sasearch over a set of PropertySource objects. The search performed is hierarchical. By default, system properties have precedence over environment variables.
Most importantly, the entire mechanism is configurable. Perhaps you have a custom source of properties that you’d like to integrate into this search. No problem — simply implement and instantiate your own PropertySource and add it to the set of PropertySources for the current Environment.
The @PropertySource annotation provides a convenient and declarative mechanism for adding a PropertySource to Spring’s Environment. Any ${...} placeholders present in a @PropertySource resource location will be resolved against the set of property sources already registered against the environment.
#### ResourcesSpring’s *Resource* interface is meant to be a more capable interface for abstracting access to low- level resources. There are a number of Resource implementations that come supplied straight out of the box in Spring:
* UrlResource
* ClassPathResource
* FileSystemResource
* ServletContextResource
* InputStreamResource
* ByteArrayResource

The *ResourceLoader* interface is meant to be implemented by objects that can return (i.e. load) Resource instances. All application contexts implement the ResourceLoader interface, and therefore all application contexts may be used to obtain Resource instances. When you call getResource() on a specific application context, and the location path specified doesn’t have a specific prefix, you will get back a Resource type that is appropriate to that particular application context. You can force specific type of Resource, regardless of the application context type, by specifying special prefix:

|Prefix|Example|Explanation|
|------|-------|-----------|
|classpath:|classpath:com/myapp/config.xml|Loaded from the classpath.|
|file:|file:///data/config.xml|Loaded as a URL, from the filesystem.|
|http:|http://myserver/log.png|Loaded as a URL.|
|(none)|/data/config.xml|Depends on the underlying ApplicationContext.|

The *ResourceLoaderAware* interface is a special marker interface, identifying objects that expect to be provided with a ResourceLoader reference. When a class implements ResourceLoaderAware and is deployed into an application context (as a Spring-managed bean), it is recognized as ResourceLoaderAware by the application context. The application context will then invoke the setResourceLoader(ResourceLoader), supplying itself as the argument (remember, all application contexts in Spring implement the ResourceLoader interface). Of course, since an ApplicationContext is a ResourceLoader, the bean could also implement the ApplicationContextAware interface and use the supplied application context directly to load resources, but in general, it’s better to use the specialized ResourceLoader interface if that’s all that’s needed. The code would just be coupled to the resource loading interface, which can be considered a utility interface, and not the whole Spring ApplicationContext interface.

As of Spring 2.5, you can rely upon autowiring of the ResourceLoader as an alternative to implementing the ResourceLoaderAware interface. The "traditional" constructor and byType autowiring modes (as described in the section called “Autowiring collaborators”) are now capable of providing a dependency of type ResourceLoader for either a constructor argument or setter method parameter respectively. For more flexibility (including the ability to autowire fields and multiple parameter methods), consider using the new annotation-based autowiring features. In that case, the ResourceLoader will be autowired into a field, constructor argument, or method parameter that is expecting the ResourceLoader type as long as the field, constructor, or method in question carries the @Autowired annotation.

If the bean itself is going to determine and supply the resource path through some sort of dynamic process, it probably makes sense for the bean to use the ResourceLoader interface to load resources. Consider as an example the loading of a template of some sort, where the specific resource that is needed depends on the role of the user. If the resources are static, it makes sense to eliminate the use of the ResourceLoader interface completely, and just have the bean expose the Resource properties it needs, and expect that they will be injected into it. For example:

```
@Value("classpath:templates/home.html")
private Resource template;
```

**FileSystemResource Caveats**

A FileSystemResource that is not attached to a FileSystemApplicationContext (that is, a FileSystemApplicationContext is not the actual ResourceLoader) will treat absolute vs. relative paths as you would expect. Relative paths are relative to the current working directory, while absolute paths are relative to the root of the filesystem.

For backwards compatibility (historical) reasons however, this changes when the FileSystemApplicationContext is the ResourceLoader. The FileSystemApplicationContext simply forces all attached FileSystemResource instances to treat all location paths as relative, whether they start with a leading slash or not.

*In practice, if true absolute filesystem paths are needed, it is better to forgo the use of absolute paths with FileSystemResource / FileSystemXmlApplicationContext, and just force the use of a UrlResource, by using the file: URL prefix.*


#### Validation, Data Binding, and Type Conversion

There are pros and cons for considering validation as business logic, and Spring offers a design for validation (and data binding) that does not exclude either one of them. Specifically validation should not be tied to the web tier, should be easy to localize and it should be possible to plug in any validator available. Considering the above, Spring has come up with a Validator interface that is both basic and eminently usable in every layer of an application.
Data binding is useful for allowing user input to be dynamically bound to the domain model of an application (or whatever objects you use to process user input). Spring provides the so-called DataBinder to do exactly that. The Validator and the DataBinder make up the validation package, which is primarily used in but not limited to the MVC framework.


#### Spring Expression Language

The Spring Expression Language (SpEL for short) is a powerful expression language that supports *querying and manipulating an object graph at runtime*. The expression language supports the following functionality:

* Literal expressions
* Boolean and relational operators
* Regular expressions
* Class expressions
* Accessing properties, arrays, lists, maps
* Method invocation
* Relational operators
* Assignment
* Calling constructors
* Bean references
* Array construction
* Inlineclists
* Inline maps
* Ternary operator
* Variables
* User defined functions
* Collection projection
* Collection selection
* Templated expressions

The more common usage of SpEL is to provide an expression string that is evaluated against a specific object instance (called the root object).

**SpEL expressions can be used with XML or annotation-based configuration metadata for defining BeanDefinitions. In both cases the syntax to define the expression is of the form #{\<expression string\>}.**
The variable systemProperties is predefined, so you can use it in your expressions. Note that you do not have to prefix the predefined variable with the # symbol in this context.

#### AOP

Aspect-Oriented Programming (AOP) complements Object-Oriented Programming (OOP) by providing another way of thinking about program structure. The key unit of modularity in OOP is the *class*, whereas in AOP the unit of modularity is the *aspect*. Aspects enable the modularization of concerns such as transaction management that cut across multiple types and objects. (Such concerns are often termed *cross-cutting concerns* in AOP literature.)

Some central AOP concepts and terminology:

* Aspect: a modularization of a concern that cuts across multiple classes. Transaction management is a good example of a crosscutting concern in enterprise Java applications. In Spring AOP, aspects are implemented using regular classes (the schema-based approach) or regular classes annotated with the @Aspect annotation (the @AspectJ style).
* Join point: a point during the execution of a program, such as the execution of a method or the handling of an exception. In Spring AOP, a join point always represents a method execution.
* Advice: action taken by an aspect at a particular join point. Different types of advice include "around," "before" and "after" advice. (Advice types are discussed below.) Many AOP frameworks, including Spring, model an advice as an interceptor, maintaining a chain of interceptors around the join point.
* Pointcut: a predicate that matches join points. Advice is associated with a pointcut expression and runs at any join point matched by the pointcut (for example, the execution of a method with a certain name). The concept of join points as matched by pointcut expressions is central to AOP, and Spring uses the AspectJ pointcut expression language by default.
* Introduction: declaring additional methods or fields on behalf of a type. Spring AOP allows you to introduce new interfaces (and a corresponding implementation) to any advised object. For example, you could use an introduction to make a bean implement an IsModified interface, to simplify caching. (An introduction is known as an inter-type declaration in the AspectJ community.)
* Target object: object being advised by one or more aspects. Also referred to as the advised object. Since Spring AOP is implemented using runtime proxies, this object will always be a proxied object.
* AOP proxy: an object created by the AOP framework in order to implement the aspect contracts (advise method executions and so on). In the Spring Framework, an AOP proxy will be a JDK dynamic proxy or a CGLIB proxy.
* Weaving: linking aspects with other application types or objects to create an advised object. This can be done at compile time (using the AspectJ compiler, for example), load time, or at runtime. Spring AOP, like other pure Java AOP frameworks, performs weaving at runtime.

Types of advice:

* Before advice: Advice that executes before a join point, but which does not have the ability to prevent execution flow proceeding to the join point (unless it throws an exception).
* After returning advice: Advice to be executed after a join point completes normally: for example, if a method returns without throwing an exception.
* After throwing advice: Advice to be executed if a method exits by throwing an exception.
* After (finally) advice: Advice to be executed regardless of the means by which a join point exits (normal or exceptional return).
* Around advice: Advice that surrounds a join point such as a method invocation. This is the most powerful kind of advice. Around advice can perform custom behavior before and after the method invocation. It is also responsible for choosing whether to proceed to the join point or to shortcut the advised method execution by returning its own return value or throwing an exception.

*Around advice is the most general kind of advice. Since Spring AOP, like AspectJ, provides a full range of advice types, we recommend that you use the least powerful advice type that can implement the required behavior.* For example, if you need only to update a cache with the return value of a method, you are better off implementing an after returning advice than an around advice, although an around advice can accomplish the same thing. Using the most specific advice type provides a simpler programming model with less potential for errors. For example, you do not need to invoke the proceed() method on the JoinPoint used for around advice, and hence cannot fail to invoke it.

Aspect-oriented programming aims to encapsulate *cross-cutting concerns* into aspects to retain modularity. This allows for the clean isolation and reuse of code addressing the cross-cutting concern.

*In aspect-oriented programming, cross-cutting concerns are aspects of a program that affect other concerns. These concerns often cannot be cleanly decomposed from the rest of the system in both the design and implementation, and can result in either scattering (code duplication), tangling (significant dependencies between systems), or both.*

**Spring AOP is proxy-based.** It is vitally important that you grasp the semantics of what that last statement actually means before you write your own aspects or use any of the Spring AOP-based aspects supplied with the Spring Framework. Spring AOP defaults to using standard *JDK dynamic proxies* for AOP proxies. This enables any interface (or set of interfaces) to be proxied. Spring AOP can also use *CGLIB proxies*. This is necessary to proxy classes rather than interfaces. CGLIB is used by default if a business object does not implement an interface. As it is good practice to program to interfaces rather than classes; business classes normally will implement one or more business interfaces.

*Spring AOP currently supports only method execution join points (advising the execution of methods on Spring beans)*. Field interception is not implemented, although support for field interception could be added without breaking the core Spring AOP APIs. If you need to advise field access and update join points, consider a language such as AspectJ.

##### Interceptors, Filters, and AOP

*HandlerInterceptor* is basically similar to a *Servlet Filter*, but in contrast to the latter it just allows custom pre-processing with the option of prohibiting the execution of the handler itself, and custom post-processing. Filters are more powerful, for example they allow for exchanging the request and response objects that are handed down the chain. Note that a filter is a servlet component, while a interceptor is a Spring component.

As a basic guideline, fine-grained handler-related preprocessing tasks are candidates for HandlerInterceptor implementations, especially factored-out common handler code and authorization checks. On the other hand, a Filter is well-suited for request content and view content handling, like multipart forms and GZIP compression. This typically shows when one needs to map the filter to certain content types (e.g. images), or to all requests.

### Data Access

### The Web

#### Web MVC Framework

The Spring Web model-view-controller (MVC) framework is designed around a DispatcherServlet that dispatches requests to handlers, with configurable handler mappings, view resolution, locale, time zone and theme resolution as well as support for uploading files.

##### DispatcherServlet

The class is [DispatcherServlet](http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/web/servlet/DispatcherServlet.html) central dispatcher for HTTP request handlers/controllers, e.g. for web UI controllers or HTTP-based remote service exporters. Dispatches to registered handlers for processing a web request, providing convenient mapping and exception handling facilities.

##### ServletContainerInitializer & WebApplicationInitializer

Servlet 3.0 [ServletContainerInitializer](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletContainerInitializer.html?is-external=true) designed to support code-based configuration of the servlet container using Spring's WebApplicationInitializer SPI as opposed to (or possibly in combination with) the traditional web.xml-based approach.

*ServletContainerInitializer* Interface which allows a library/runtime to be notified of a web application's startup phase and perform any required programmatic registration of servlets, filters, and listeners in response to it. In Spring, the class [SpringServletContainerInitializer](http://docs.spring.io/autorepo/docs/spring-framework/current/javadoc-api/org/springframework/web/SpringServletContainerInitializer.html#onStartup-java.util.Set-javax.servlet.ServletContext-) implements this interface. In Spring Boot, the class *TomcatStarter* (org.springframework.boot.context.embedded.tomcat.TomcatStarter) also implements this interface.

*WebApplicationInitializer* Interface to be implemented in Servlet 3.0+ environments in order to configure the ServletContext programmatically -- as opposed to (or possibly in conjunction with) the traditional web.xml-based approach. Implementations of this SPI will be detected automatically by *SpringServletContainerInitializer*, which itself is bootstrapped automatically by any Servlet 3.0 container.

Spring's [WebApplicationInitializer](http://docs.spring.io/autorepo/docs/spring-framework/current/javadoc-api/org/springframework/web/WebApplicationInitializer.html) SPI consists of just one method: WebApplicationInitializer.onStartup(ServletContext). The signature is intentionally quite similar to ServletContainerInitializer.onStartup(Set, ServletContext): simply put, SpringServletContainerInitializer is responsible for instantiating and delegating the ServletContext to any user-defined WebApplicationInitializer implementations. It is then the responsibility of each WebApplicationInitializer to do the actual work of initializing the ServletContext. 

**The class SpringServletContainerInitializer is neither designed for extension nor intended to be extended. It should be considered an internal type, with WebApplicationInitializer being the public-facing SPI.**

The class [ServletContextInitializer](http://docs.spring.io/autorepo/docs/spring-boot/current/api/org/springframework/boot/context/embedded/ServletContextInitializer.html) Interface used to configure a Servlet 3.0+ context programmatically. Unlike WebApplicationInitializer, classes that implement this interface (and do not implement WebApplicationInitializer) will not be detected by SpringServletContainerInitializer and hence will not be automatically bootstrapped by the Servlet container. This interface is primarily designed to allow ServletContextInitializers to be managed by Spring and not the Servlet container.

**When you make your Spring Boot application as an executable jar with an embedded Tomcat 7, the WebApplicationInitialier is NOT called when the application is started. Instead, you need to create a bean which implements the [ServletContextInitializer](http://docs.spring.io/autorepo/docs/spring-boot/current/api/org/springframework/boot/context/embedded/ServletContextInitializer.html) interface.** See:

* <https://github.com/spring-projects/spring-boot/issues/522>
* <https://github.com/spring-projects/spring-boot/issues/321>
* <http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-embedded-container-servlets-and-filters>

##### Handling Exceptions

#### View Technologies

#### WebSocket Support

### Spring IO Platform

The Spring IO platform includes Foundation Layer modules and Execution Layer domain-specific runtimes (DSRs). The Foundation layer represents the core Spring modules and associated third-party dependencies that have been harmonized to ensure a smooth development experience. The DSRs provided by the Spring IO Execution Layer dramatically simplify building production-ready, JVM-based workloads. See <http://spring.io/platform>.

![Spring IO Platform](https://github.com/rkq/docs/blob/master/pics/java_platform_spring_io_architecture.png)



### Spring Boot

### Spring Security

Security is an ever-moving target, and it’s important to pursue a comprehensive, system-wide approach. In security circles we encourage you to adopt "layers of security", so that each layer tries to be as secure as possible in its own right, with successive layers providing additional security. The "tighter" the security of each layer, the more robust and safe your application will be. At the bottom level you’ll need to deal with issues such as transport security and system identification, in order to mitigate man-in-the-middle attacks. Next you’ll generally utilise firewalls, perhaps with VPNs or IP security to ensure only authorised systems can attempt to connect. In corporate environments you may deploy a DMZ to separate public-facing servers from backend database and application servers. Your operating system will also play a critical part, addressing issues such as running processes as non-privileged users and maximising file system security. An operating system will usually also be configured with its own firewall. Hopefully somewhere along the way you’ll be trying to prevent denial of service and brute force attacks against the system. An intrusion detection system will also be especially useful for monitoring and responding to attacks, with such systems able to take protective action such as blocking offending TCP/IP addresses in real-time. Moving to the higher layers, your Java Virtual Machine will hopefully be configured to minimize the permissions granted to different Java types, and then your application will add its own problem domain-specific security configuration. *Spring Security makes this latter area - application security - much easier.*

As you probably know two major areas of application security are *"authentication"* and *"authorization" (or "access-control")*. These are the two main areas that Spring Security targets. "Authentication" is the process of establishing a principal is who they claim to be (a "principal" generally means a user, device or some other system which can perform an action in your application)."Authorization" refers to the process of deciding whether a principal is allowed to perform an action within your application. To arrive at the point where an authorization decision is needed, the identity of the principal has already been established by the authentication process. These concepts are common, and not at all specific to Spring Security.

Core components:

* SecurityContextHolder, to provide access to the SecurityContext.
* SecurityContext, to hold the Authentication and possibly request-specific security information.
* Authentication, to represent the principal in a Spring Security-specific manner.
* GrantedAuthority, to reflect the application-wide permissions granted to a principal.
* UserDetails, to provide the necessary information to build an Authentication object from your application’s DAOs or other source of security data.
* UserDetailsService, to create a UserDetails when passed in a String-based username (or certificate ID or the like).

Core services:

* AuthenticationManager, ProviderManager and AuthenticationProvider
* Password Encoding

The AuthenticationManager is just an interface, so the implementation can be anything we choose. The default implementation in Spring Security is called ProviderManager and rather than handling the authentication request itself, it delegates to a list of configured AuthenticationProvider s, each of which is queried in turn to see if it can perform the authentication. Each provider will either throw an exception or return a fully populated Authentication object. The most common approach to verifying an authentication request is to load the corresponding UserDetails and check the loaded password against the one that has been entered by the user. This is the approach used by the DaoAuthenticationProvider. The loaded UserDetails object - and particularly the GrantedAuthority s it contains - will be used when building the fully populated Authentication object which is returned from a successful authentication and stored in the SecurityContext.


With above components and services, the authentication process will look like below  (using user name and passwordauthentication as an example):

1. The username and password are obtained and combined into an instance of UsernamePasswordAuthenticationToken (an instance of the Authentication interface, which we saw earlier).
2. The token is passed to an instance of AuthenticationManager for validation.
3. The AuthenticationManager returns a fully populated Authentication instance on successful authentication.
4. The security context is established by calling SecurityContextHolder.getContext().setAuthentication(…​), passing in the returned authentication object.

#### Web Application Security

##### The Security Filter Chain

Spring Security’s web infrastructure is based entirely on standard servlet filters. It doesn’t use servlets or any other servlet-based frameworks (such as Spring MVC) internally, so it has no strong links to any particular web technology. It deals in HttpServletRequest s and HttpServletResponse s and doesn’t care whether the requests come from a browser, a web service client, an HttpInvoker or an AJAX application.

Spring Security maintains a filter chain internally where each of the filters has a particular responsibility and filters are added or removed from the configuration depending on which services are required. **The ordering of the filters is important as there are dependencies between them.** If you have been using *namespace configuration*, then the filters are automatically configured for you and you don’t have to define any Spring beans explicitly but here may be times when you want full control over the security filter chain, either because you are using features which aren’t supported in the namespace, or you are using your own customized versions of classes.

In Spring Security, the filter classes are also Spring beans defined in the application context and thus able to take advantage of Spring’s rich dependency-injection facilities and lifecycle interfaces. Spring’s **DelegatingFilterProxy** provides the link between web.xml and the application context.

```
<filter>
    <filter-name>myFilter</filter-name>
    <filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
</filter>

<filter-mapping>
    <filter-name>myFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

Notice that the filter is actually a DelegatingFilterProxy, and not the class that will actually implement the logic of the filter. What DelegatingFilterProxy does is delegate the Filter’s methods through to a bean which is obtained from the Spring application context. This enables the bean to benefit from the Spring web application context lifecycle support and configuration flexibility. The bean must implement javax.servlet.Filter and it must have the same name as that in the filter-name element.

Spring Security’s web infrastructure should only be used by delegating to an instance of **FilterChainProxy**. The security filters should not be used by themselves. In theory you could declare each Spring Security filter bean that you require in your application context file and add a corresponding DelegatingFilterProxy entry to web.xml for each filter, making sure that they are ordered correctly, but this would be cumbersome and would clutter up the web.xml file quickly if you have a lot of filters. FilterChainProxy lets us add a single entry to web.xml and deal entirely with the application context file for managing our web security beans. It is wired using a DelegatingFilterProxy, just like in the example above, but with the filter-name set to the bean name **"filterChainProxy"**. The filter chain is then declared in the application context with the same bean name. Here’s an example:

```
<bean id="filterChainProxy" class="org.springframework.security.web.FilterChainProxy">
<constructor-arg>
	<list>
	<sec:filter-chain pattern="/restful/**" filters="
		securityContextPersistenceFilterWithASCFalse,
		basicAuthenticationFilter,
		exceptionTranslationFilter,
		filterSecurityInterceptor" />
	<sec:filter-chain pattern="/**" filters="
		securityContextPersistenceFilterWithASCTrue,
		formLoginFilter,
		exceptionTranslationFilter,
		filterSecurityInterceptor" />
	</list>
</constructor-arg>
</bean>
```

*Note that FilterChainProxy does not invoke standard filter lifecycle methods on the filters it is configured with. We recommend you use Spring’s application context lifecycle interfaces as an alternative, just as you would for any other Spring bean.*

The order that filters are defined in the chain is very important. Irrespective of which filters you are actually using, the order should be as follows:

* ChannelProcessingFilter, because it might need to redirect to a different protocol
* SecurityContextPersistenceFilter, so a SecurityContext can be set up in the SecurityContextHolder at the beginning of a web request, and any changes to the SecurityContext can be copied to the HttpSession when the web request ends (ready for use with the next web request)
* ConcurrentSessionFilter, because it uses the SecurityContextHolder functionality and needs to update the SessionRegistry to reflect ongoing requests from the principal
* Authentication processing mechanisms - UsernamePasswordAuthenticationFilter, CasAuthenticationFilter, BasicAuthenticationFilter etc - so that the SecurityContextHolder can be modified to contain a valid Authentication request token
* The SecurityContextHolderAwareRequestFilter, if you are using it to install a Spring Security aware HttpServletRequestWrapper into your servlet container
* The JaasApiIntegrationFilter, if a JaasAuthenticationToken is in the SecurityContextHolder this will process the FilterChain as the Subject in the JaasAuthenticationToken
* RememberMeAuthenticationFilter, so that if no earlier authentication processing mechanism updated the SecurityContextHolder, and the request presents a cookie that enables remember-me services to take place, a suitable remembered Authentication object will be put there
* AnonymousAuthenticationFilter, so that if no earlier authentication processing mechanism updated the SecurityContextHolder, an anonymous Authentication object will be put there
* ExceptionTranslationFilter, to catch any Spring Security exceptions so that either an HTTP error response can be returned or an appropriate AuthenticationEntryPoint can be launched
* FilterSecurityInterceptor, to protect web URIs and raise exceptions when access is denied


*If you’re using some other framework that is also filter-based, then you need to make sure that the Spring Security filters come first. This enables the SecurityContextHolder to be populated in time for use by the other filters. Examples are the use of SiteMesh to decorate your web pages or a web framework like Wicket which uses a filter to handle its requests.*

When we looked at how to set up web security using namespace configuration, we used a DelegatingFilterProxy with the name "springSecurityFilterChain". You should now be able to see that this is the name of the FilterChainProxy which is created by the namespace.


## Frameworks - Netty

Netty is an *asynchronous event-driven* network application framework 
for rapid development of maintainable high performance protocol servers & clients. See <http://netty.io>.

![Netty Archetecture](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_architecture.png)

Key components:

* Bootstrap and ServerBootstrap, A Netty application begins by setting up one of the bootstrap classes, which provide a container for the configuration of the application's network layer.
* Channel, To be somewhat formal about it, the underlying network transport API must provide applications with a construct that implements I/O operations: read, write, connect, bind and so forth. For us, this construct is pretty much always going to be a "socket". Netty's interface Channel defines the semantics for interacting with sockets by way of a rich set of operations: bind, close, config, connect, isActive, isOpen, isWritable, read, write and others. Netty provides numerous Channel implementations for specialized use. These include AbstractChannel, AbstractNioByteChannel, AbstractNioChannel, EmbeddedChannel, LocalServerChannel, NioSocketChannel and many more.
* ChannelHandler, ChannelHandlers support a variety of protocols and provide containers for data-processing logic. We have already seen that a ChannelHandler is triggered by a specific event or set of events. Note that the use of the generic term "event" is intentional, since a ChannelHandler can be dedicated to almost any kind of action - converting an object to bytes (or the reverse), or handling exceptions thrown during processing. One interface you'll be encountering (and implementing) frequently is ChannelInboundHandler. This type receives inbound events (including received data) that will be handled by your application's business logic. You can also flush data from a ChannelInboundHandler when you have to provide a response. In short, the business logic of your application typically lives in one or more ChannelInboundHandlers.
* ChannelPipeline, A ChannelPipeline provides a container for a chain of ChannelHandlers and presents an API for managing the flow of inbound and outbound events along the chain. Each Channel has its own ChannelPipeline, created automatically when the Channel is created. How do ChannelHandlers get installed in the ChannelPipeline? This is the role of abstract ChannelInitializer, which implements ChannelHandler. A subclass of ChannelInitializer is registered with a ServerBootstrap. When its method initChannel() is called, this object will install a custom set of ChannelHandlers in the pipeline. When this operation is completed, the ChannelInitializer subclass then automatically removes itself from the ChannelPipeline.
* EventLoop, An EventLoop processes I/O operations for a Channel. A single EventLoop will typically handle events for multiple Channels. An EventLoopGroup may contain more than one EventLoop and provides an iterator for retrieving the next one in the list.
* ChannelFuture, All I/O operations in Netty are asynchronous. Since an operation may not return immediately we need to have a way to determine its result at a later time. For this purpose Netty provides interface ChannelFuture, whose addListener method registers a ChannelFutureListener to be notified when an operation has completed (whether successfully or not).

### Transports

Netty comes bundled with a several transports that are ready for use. Not all of them support all protocols. This means the transport you select needs to be compatible with underlying protocol employed by your application.

**NIO Nonblocking I/O**

NIO provides a fully asynchronous implementation of all I/O operations. At it's base is the selector approach that has been available in since the NIO subsystem was introduced in JDK 1.4.

The basic concept of the selector is to register to receive notification when the state of a Channel changes. The possible state changes are:* A new Channel was accepted and is ready.
* A Channel connection was completed.* A Channel has data that is ready for reading.* A Channel is available for writing data.
![NIO](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_nio.png)
A feature that is currently available only with NIO transport is called zero-file-copy, which allows you to quickly and efficiently transfer content from a file system by moving data to the network stack without copying from kernel space to user space. This can make a big difference in protocols such as FTP or HTTP.

**OIO Old Blocking I/O**

In Netty, the OIO transport represents a compromise. It is accessed via Netty's common API but is not asynchronous, being built on the blocking implementation of java.net.

In the java.net API you usually have one thread that accepts new connections arriving at the listening ServerSocket and creating a new thread to handle the traffic on the new Socket. This is required since every I/O operation on a specific socket may block at any time. Handling multiple sockets with a single thread could easily lead to a blocking operation on one socket tying up all the others as well.Given this, you may wonder how Netty can support NIO with the same API used for asynchronous transports. Here Netty makes use of the SO_TIMEOUT flag that can be set on a Socket. This timeout specifies the maximum number of milliseconds to wait for an I/O operation to complete. If the operation fails to complete within the specified interval, a SocketTimeoutException is thrown. Netty catches this exception and continues the processing loop. On the next EventLoop run, it tries again. This is in fact the only way an asynchronous framework like Netty can support OIO. The problem with this approach is the cost of filling in the stack trace when a SocketTimeoutException is thrown.

![OIO](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_oio.png)

**Local Transport for Communication within a JVM**

Netty provides a "local" transport for asynchronous communication between clients and servers running in the same Java Virtual Machine. This transport supports the API common to all Netty transport implementations.
In this transport the SocketAddress associated with a server Channel is not "bound" to a physical network address, rather it is stored in a registry for as long as the server is running and deregistered when the Channel is closed. Since the transport does not accept "real" network traffic, it can't interoperate with other transport implementations. Therefore, a client that wishes to connect to a server that uses local transport must use it as well. Apart from this limitation, its use is identical to that of other transports.
**Embedded Transport**
Netty also provides a transport that allows you to embed ChannelHandler instances in other ChannelHandlers and use them like helper classes, adding flexibility to the ways in which you can interact with your ChannelHandlers.
This embedding technique is typically used for testing ChannelHandler implementations, but it can also be employed to add functionality to an existing ChannelHandler without requiring code changes. The key to the embedded transport is a concrete Channel implementation not surprisingly called "EmbeddedChannel".
#### Transport Use Cases
![Transport-Protocol](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_transport_protocol.png)
**NON-BLOCKING CODE-BASE**
If you don't have blocking calls in your code base - or can limit them - it is always a good idea to use NIO. While NIO is intended to handle many concurrent connections it also works out quite well with a smaller number, especially given the way it shares threads across connections.**BLOCKING CODE BASE**
If your code base relies heavily on blocking I/O and your applications have a corresponding design, you are likely to encounter problems with blocking operations if you try to convert directly to Netty's NIO transport. Rather than rewriting your code to accomplish this, consider a phased migration: start with with OIO and move to NIO once you have revised your code.**COMMUNICATIONS WITHIN THE SAME JVM**
Communications within the same JVM with no need to expose a service over the network present the perfect use case for local transport. This will eliminate all the overhead of real network operations while still employing your Netty code base.If the need arises later to expose the service over the network you will need only to replace the transport with NIO or OIO. You may also find it useful to add an extra encoder and decoder to convert Java objects to and from ByteBuf.**TESTING YOUR CHANNELHANDLER IMPLEMENTATIONS**
If you want to write unit tests for your ChannelHandler implementations, consider using the embedded transport. This will make it easy to test your code without having to create many mock objects. Your classes will still conform to the common API event flow, guaranteeing that the ChannelHandler will work correctly with "live" transports.
### Buffers
Netty uses *reference-counting* to determine when to release a *ByteBuf* or *ByteBufHolder* and any associated resources, thereby enabling the use of pooling and other techniques to improve performance and reduce memory consumption.

### ChannelHandler and ChannelPipeline
Netty provides powerful support for the data-processing areas of application development. The ChannelHandlers can be chained together in a ChannelPipeline to structure processing steps in a flexible and modular fashion. It involves ChannelHandler, ChannelPipeline and an important related class, ChannelHandlerContext.
Netty defines these two important subinterfaces of ChannelHandler:
* ChannelInboundHandler - processes inbound data and state changes of all kinds.
* ChannelOutboundHandler - processes outbound data and allows interception of allkinds of operations.
Netty provides a simple skeleton implementation of ChannelHandler that has bodies for all of the declared method signatures. The methods of this class, *ChannelHandlerAdapter*, merely forward events to the next ChannelHandler in the pipeline until the end of the pipeline is reached. This class also serves as the base for *ChannelInboundHandlerAdapter* and *ChannelOutboundHandlerAdapter*.*All three adapter classes are intended to serve as starting points for your own implementations; you can extend them, overriding only the methods you need to customize.*
#### ChannelInboundHandler
**Please note that a ChannelInboundHandler implementation that overrides channelRead() to process incoming messages is responsible for releasing resources. Netty uses pooled resources for ByteBuf, so failing to release resources will lead to a memory leak.**
Netty logs unreleased resources with a WARN-level log entry, making it fairly simple to find offending instances in the code. However, since managing resources by hand can be cumbersome, you can simplify matters by using SimpleChannelInboundHandler. Please note: since SimpleChannelInboundHandler releases resources automatically, do not store references to any messages for later use, as these will become invalid.
#### ChannelOutboundHandler
A powerful aspect of ChannelOutboundHandler's role is its ability to defer an operation or event on request. This enables some sophisticated approaches to request handling. For example, you can defer flush operations if writing to the remote peer is suspended and pick them up at a later time.
*ChannelPromise vs. ChannelFuture*A ChannelPromise is a special ChannelFuture that allows you to either fail or success the ChannelPromise and so the operation to which it belongs. So whenever you call for example Channel.write() a new ChannelPromise will be created and passed throught the ChannelPipeline. The write itself will just return a ChannelFuture and so only allow you to get notified once the operation completes. Netty itself will use the ChannelPromise to be able to notify the returned ChannelFuture, which in fact is most of the times just the ChannelPromise itself (ChannelPromise extends ChannelFuture).
#### Resource Management
Whenever you act on data via ChannelInboundHandler.channelRead(...) or ChannelOutboundHandler.write(...) it is important to understand how you need to handle resources to ensure there are no resource leaks.
Netty uses reference counting to handle pooled ByteBufs. Thus it is important to make sure the reference count is adjusted after a ByteBuf is completely processed.
One of the tradeoffs of reference-counting is that the user have to be carefully when consume messages. While the JVM will still be able to GC such a message (as it is not aware of the reference-counting) this message will not be put back in the pool from which it may be obtained before. Thus chances are good that you will run out of resources at one point if you do not carefully release these messages.To make it easier for the user to find missing releases Netty contains a so called ResourceLeakDetector which will sample about 1% of buffer allocations to check if there is a leak in your application. Because of the 1% sampling, the overhead is quite small.*SimpleChannelInboundHandler consuming inbound messages the easy way*As consuming inbound data and releasing it is such a common task Netty provides you with a special ChannelInboundHandler implementation called SimpleChannelInboundHandler. This implementation will automatically release a message once it was consumed by the user via the channelRead0() method.
if you handle a write operation and discard a message you are responsible for releasing it. Now let's look at how you could make use of this in practice.
It's important to remember to release resources and notify the ChannelPromise. If the ChannelPromise is not notified it may lead to situations where a ChannelFutureListener is not notified about a handled message.
So let us summarize this; It is the responsibility of the user to call ReferenceCountUtil.release(message) if a message is consumed/discarded and not passed to the next ChannelOutboundHandler in the ChannelPipeline. Once the message is passed over to the actual transport it will be released automatically by it once the message was written or the Channel was closed.
#### ChannelPipeline

If we think of a ChannelPipeline simply as a series of ChannelHandler instances that intercept the inbound and outbound events that flow through a Channel, then it is easy to see how the interaction of these ChannelHandlers can provide the core of an application's data and event processing logic.
Every new Channel that is created is assigned a new ChannelPipeline. This association is permanent; the Channel can neither attach another ChannelPipeline nor detach the current one. This is a fixed aspect of Netty's component lifeycle and requires no action on the part of the developer.
Depending on its origin, an event will be handled by either a ChannelInboundHandler or a ChannelOutboundHandler. Subsequently it will be forwarded to the next handler of the same supertype by a call to a ChannelHandlerContext implementation.
![ChannelPipeline](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_channelpipeline.png)
A ChannelHandler can modify the layout of a ChannelPipeline in real time by adding, removing or replacing other ChannelHandlers. (It can remove itself from the ChannelPipeline as well.) This is one of the most important capabilities of the ChannelHandler so let's take a look at how it is done.
**ChannelHandler execution in the ChannelPipeline and blocking**Normally each ChannelHandler that is added to the ChannelPipeline will process the event that is passed through it its EventLoop (the I/O thread). It is critically important not to block this thread as it would have a negative effect on the overall handling of I/O.
Sometimes it may be necessary to interface with legacy code that uses blocking APIs. For this case the ChannelPipeline has add() methods that accept an EventExecutorGroup. If a custom EventExecutorGroup is passed in the event it will be handled by one of the EventExecutor contained in this EventExecutorGroup and so moved away from the EventLoop of the Channel itself. A default implementation which is called *DefaultEventExecutorGroup* comes as part of Netty.#### ChannelHandlerContext
The interface ChannelHandlerContext represents an association between a ChannelHandler and a ChannelPipeline, and an instance is created whenever a ChannelHandler is added to a ChannelPipeline. The primary function of ChannelHandlerContext to manage the interaction of the ChannelHandler with which it is associatedwithotherChannelHandlersin thesameChannelPipeline.
ChannelHandlerContext has numerous methods, some of which are also present on Channel and ChannelPipeline itself. However, if you invoke these methods on a Channel or ChannelPipeline instance they propagate through the entire pipeline. By contrast, the same method called on a ChannelHandlerContext starts at the current associated ChannelHandler and propagates only to the next ChannelHandler in the pipeline capable of handling the event.
![ChannelHandlerContext](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_channelhandlercontext.png)
Additional notes:
* The ChannelHandlerContext associated with a ChannelHandler never changes so it is safe to cache a reference to it.
* The hannelHandlerContext methods involve a shorter event flow than the same methods available on other classes. This should be exploited where possible to provide the best performance.**Why share a ChannelHandler?**
A common reason for installing a single ChannelHandler in multiple ChannelPipelines is to gather statistics across multiple Channels.
### The Codec Framework
Every network application has to define how raw bytes transferred between peers are to be parsed and converted to - and from - the target program's data format. This conversion logic will be handled by a "codec," which consists of a "decoder" and an "encoder".Both decoders and encoders transform one sequence of bytes to another. How do we distinguish them?Think of a "message" as a structured sequence of bytes having semantic meaning for a specific application - its "data". The encoder is the component that converts that message to a format suitable for transmission (most likely a byte stream), while the corresponding decoder transforms the transmitted data back to the program's message format. It is logical, then, to think of conversion "from" a message as operating on outbound data, while conversion "to" a message is handling inbound data.
#### Decoders
Netty has a rich set of abstract base classes that simplify the writing of decoders. These cover two distinct use cases:
* decoding from bytes to message (ByteToMessageDecoder and ReplayingDecoder)
* decoding from message to message (MessageToMessageDecoder)

A Netty decoder is an abstract implementation of ChannelInboundHandler.


#### Encoders

An encoder trasforms outbound data from one format to another, thus it implements ChanneOutboundHandler. 

Netty offers a set of classes to help you to write encoders. Not surprisingly, they address the reverse of the decoder functions:

* encoding from message to bytes
* encoding from message to message


### Bootstrapping

In the simplest terms, bootstrapping is the process of configuring an application. Netty's classes for bootstrapping clients and servers insulate your application code from the network infrastructure, connecting and enabling all of the components in the background.

Netty includes two different types of bootstraps. Rather than just thinking of them as "server" and "client" bootsraps, it is more useful to consider the application functions they are intended to support. In this sense, "servers" are applications that devote a "parent" channel to accepting connections and create "child" channels for them, while a "client" will most likely require only a single, non-"parent" channel for all network interactions.

### EventLoop and Thread Model

All of your ChannelHandlers, which contain your business logic, are guaranteed to be executed by the same Thread for a specific Channel. This doesn't mean Netty fails to use multithreading, but it does pin each Channel to one Thread.

**EventLoop and EventLoopGroup**
Remember that the EventLoop assigned to the Channel is responsible for handling all the operations for the Channel. Whenever you execute a method that returns a ChannelFuture it will be executed in the EventLoop that is assigned to the Channel.The EventLoopGroup contains a number of EventLoops and assigns an EventLoop to the Channel when it is registered.

An EventLoop is powered by exactly one Thread that never changes. To make proper use of resources, Netty uses multiple EventLoops, depending on the configuration and the available cores.

One important thing about I/O and event handling in Netty 4 is that each of these I/O operations and events are always handled by the EventLoop itself and so by the Thread that's assigned to the EventLoop.

The trick that's used inside Netty to make its thread model perform so well is that it checks to see if the executing Thread is the one that's assigned to the actual Channel (and EventLoop). The EventLoop is responsible for handling all events for a Channel during its lifetime. If the calling Thread is the same as the one of the EventLoop, the code block in question is executed. If the Thread is different, it schedules a task and puts it in an internal queue, used by the EventLoop, for later execution. The EventLoop will notice that there's a queued task to process and automatically pick it up. This allows you to directly interact with the Channel from any Thread while still being sure that all ChannelHandlers don't need to worry about concurrent access.

It's important to know that each EventLoop has its own task/event queue and so is not affected by other EventLoops when processing the queue.

**That said, because of the design it's important to ensure that you never put any long-running tasks in the execution queue, because once the task is executed and run it will effectively block any other task from executing on the same thread.** How much this affects the overall system depends on the implementation of the EventLoop that's used in the specific transport implementation. Because switching between transports is possible without any changes in your code base, it's important to remember that the Golden Rule always applies here: **Never block the I/O thread**. If you must block calls (or execute tasks that can take long periods to complete), you must use a dedicated EventExecutor for your ChannelHandler.

Every once in a while, you need to schedule a task for later execution. Maybe you want to register a task that gets fired after a client is connected for five minutes. A common use case is to send an "Are you alive?" message to the remote peer to see if it's still there. If it fails to respond, you know it's not connected anymore, and you can close the channel (connection) and release the resources.

Netty uses an EventLoopGroup that contains EventLoops that will serve the I/O and events for a Channel. *The way EventLoops are created and assigned varies based on the transport implementation.* An asynchronous implementation uses only a few EventLoops (and so Threads) that are shared between the Channels. This allows a minimal number of Threads to serve many Channels, eliminating the need to have one dedicated Thread for each of them.

![Netty Eventloop](https://github.com/rkq/docs/blob/master/pics/java_platform_netty_eventloop.png)

The semantic is a bit different for other transports, such as the shipped OIO (Old Blocking I/O) transport: one EventLoop (and so one Thread) is created per Channel. But even if the semantics change in this case, one thing still stays the same: Each Channel's I/O will be handled by only one Thread at one time, which is the one Thread that powers the EventLoop of the Channel. You can depend on this hard rule; it's what makes writing code via the Netty framework so easy compared to other user network frameworks out there.

#### Scheduling Tasks for Later Execution

You can schedule tasks for later execution in Netty using its powerful EventLoop implementation. The actual implementation in Netty is based on the paper Hashed and Hierarchical Timing Wheels: Data Structures for the Efficient Implementation of a Timer Facility, by George Varghese and Tony Lauck. This kind of implementation only guarantees an approximated execution, which means that the execution of the task may not be 100% on time. This has proven to be a tolerable limitation in practice and does not affect most applications at all. It's just something to remember if you need to schedule tasks, because it may not be the perfect fit if you need 100% on-time execution.

To better understand how this works, think of it this way:

1. You schedule a task with a given delay.2. The task gets inserted into the Schedule-Task-Queue of the EventLoop.3. The EventLoop checks on every run to see if tasks need to get executed then.
4. If there's a task, the EventLoop will execute it right away and remove it from the queue.5. The EventLoop waits for the next run and starts over again with step 4.
Because of this implementation, the scheduled execution may be not 100% accurate. This is fine for most use cases given that it allows for almost no overhead within Netty.But what if you need more accurate execution? It's easy. You'll need to use another implementation of ScheduledExecutorService that's not part of Netty. Just remember that if you don't follow Netty's thread model protocol, you'll need to synchronize the concurrent access on your own. Do this only if you must.

### Netty-based Frameworks

#### Facebook Nifty and Swift

<https://github.com/facebook/nifty>

<https://github.com/facebook/swift>

#### Twitter Finagle

<https://github.com/twitter/finagle>

#### Google gRPC

<http://www.grpc.io>

<https://github.com/grpc/grpc-java>

## Middlewares

### Tomcat

<http://tomcat.apache.org>

### Jetty

<http://www.eclipse.org/jetty/>

## Toolset
### Continuous Delivery
#### Maven

<http://maven.apache.org>

<http://mvnrepository.com>

#### Jenkins

<http://jenkins-ci.org>

#### TeamCity

<https://www.jetbrains.com/teamcity/>


## Java HotSpot Virtual Machine

### Java Development Kit

**JDK 8**

[Java Platform, Standard Edition Tools Reference](http://docs.oracle.com/javase/8/docs/technotes/tools/unix/toc.html)

[JDK Tools and Utilities](http://docs.oracle.com/javase/8/docs/technotes/tools/)

**JDK 7 and Earlier Releases**

[Java HotSpot VM Options](http://www.oracle.com/technetwork/articles/java/vmoptions-jsp-140102.html)

[JDK Tools and Utilities](http://docs.oracle.com/javase/7/docs/technotes/tools/)


### Garbage Collector

[Java SE 6 HotSpot[tm] Virtual Machine Garbage Collection Tuning](http://www.oracle.com/technetwork/java/javase/gc-tuning-6-140523.html)

[Java Platform, Standard Edition HotSpot Virtual Machine Garbage Collection Tuning Guide](http://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/index.html)

### JIT Compiler

### VM Runtime

