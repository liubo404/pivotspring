# Chapter 1
## Introduction

So here you are: you want to learn how to develop web applications using Spring,and you chose this study guide to help you. This might be one of the best decisons that you could make, as this book was written not noly to help you to understatnd Spring Web, but to love it as well. This study guide may even help you pass the certification exam--if you follow al the instructions properly and do all the exercises. This study guide explores more Spring Web is all about, which you can skip reading, of course; but if you really want to learn Spring to develop web applications like a professional, then it would be wise not to skip this.


## Spring and What It Does
When building a project using Java, a lot of functionality needs to be built from scratch. But a lot of useful functionalities are already built and are free to use because of the open source world we live in. A long time ago, when the Java world was still quite small, you would say that you were using a library when you used open source code developed by somebody else, shipped as a *.jar file. But as time passed, the software development world evolved and the libraries grew too.  They became frameworks. Because they were no longer one *.jar file that you could import, they became a collection of more-or-less decoupled libraries with different responsibilities, and you had the option to import only what you needed.

Release in October 2002 as an open source framework and an inversion of control container developed using Java, Spring was built for the Java platform. It was concieved with the dependency injection software design pattern in mind, and its main purpose is to make dependency handling easier. A Java application is basically a group of objects exchanging data and influencing each other's behavior. The Spring Framework simplified the way in which objects talks to each other and the way they depend on each other. This is why Spring evangelists claim that the reason Java was invented was so that Spring would come into existence one day. The development of Java applications became easier when Spring emerged, providing comprehensive infrastructure support. Spring makes it easier to compose disparate components into a fully working application.

Spring comes with a lot of default behaviors already implemented(components called infrastructure beans are a default configuration; then can be used to create functional basic applications without extra customization), because the Spring Framework was also built with the convention over configuration paradigm as principle, which seeks to decrease the number of decisions a developer has to make when writing code, but also makes it easier for the developer to customize the behavior of objects, offering increased flexibility.

Spring is currently the VIP of Java frameworks and it has been growing exponentially, especially since 2009, when VMware acquired SpringSource, the company behind Spring. The VMware and the EMC Corporation in April 2013, now known as Pivotal, was also advantageous for Spring, as it became one of Pivotal's central elements in its strategy to provide innovative and modern software-driven experiences to its customers. Spring is now a full-blown technoloy that can be used to build enterprise-ready applications in a very short time, and it comes in 25 flavors. Figure 1-1 shows a diagram of all Spring-released projects. The following list describes these projects.


* **Spring Framework** provides core support for dependency injection, transaction management, web applications, data access, messaging, and more.
* **Spring Boot** provides compact setups for different types of applications, helping you to focus on your code instead of infrastructure configuration.
* **Spring XD** simplifies the development of Big Data applicatios.

[^n]: You can read about these projects, as well as other pojects that have not released officially(Spring Session, for example) in detail at http://spring.io/projects.

* **Spring Cloud** provides a set of tools for distributed applications.
* **Spring Data** provides a consistent approach to data access. (This study guide uses a subproject called Spring Data JPA to help us manage data easily.)
* **Spring Integration** supoorts the well-known Enterprise Integration Patterns via lightweight messaging and declarative adapters.
* **Spring Batch** simplifies and optimizes the work of processing high-volume batch operations.
* **Spring Security** provides tools for authentication and authorization. (Because _web security is one of the subjects of the certification exam_, there is a section about web security in this study guide that you will have to pay close attention to.)
* **Spring HATEOAS** provides some APIs to help the development of REST representations that follow the HATEOAS principle(Hypermedia as the Engine of Application State,which means that a client interacts with a network application entirely through hypermedia provided dynamically by application servers).
* **Spring Social** provides an API to connect Spring applications to the third-party APIs of social networks like Facebook and Twitter, as well as others.
* **Spring AMQP** provides an API for AMQP-based messaging solutions.
* **Spring Mobile** simplifies the development of mobile applications.
* **Spring for Android** provides key spring components to use in the development of Android applications.
* **Spring Web Flow** supports the building of web application with controlled navigation(Spring Web Flow is another subject in the certification exam.)
* **Spring Web Service** facilitates the development of SOAP-based applications.
* **Spring LDAP** provides tools to develop LDAP applications.
* **Grails** is a powerful open source web framework based on Groovy and inspired by Ruby on Rails. It is used to create web applications that run on the Java Virtual Machine(JVM).
* **Groovy** started as a dynamic language for the Java platform. It brings high-productiviy development features to the JVM,  and resembles Python, Ruby, Perl, and Smalltalk in regards to syntax and features. SpringSource has taken over its development and maintenance.
* **Spring Scala** mixed up Spring with Scala language features.
* **Spring Roo** helps define application templates that can be built into a full Java application within minutes.
* ** Spring  BlazeDS Integration** tools integrate Spring with Adobe BlazeDS.
* **Spring Loaded** reloads classes as files changes, boosting productivily (similar project to JRebel).

[^n]: Pivotal decided to stop funding this project in March 2015.
[^n]: Funding for this project also enned din March 2015.

* **Spring Shell** provides the capability to build command-line apps.
* **REST Shell** makes the writing and testing of RESTful application easier with CLI-based resource discovery and interaction.

## The Focus of this Study Guide
As this study guide is being written, the Spring Framework consists of features organized into about 20 modules grouped into following: Core Container, Data Access/Integration, Web, AOP(aspect-oriented programming), Instrumentation, Messaging, and Test.
   The topics covered in this study guide are Spring Framework's support components for the presentation tier(and specifically web-based presentatation tires). A bonus in this book is the Spring WebSocket chapter, which was added to the Spring Framework in version 4 and is also an optional part of the official Spring Web course not featured in the certification exam. In the Figure 1-2 you can see the SprngMVC stack, a tiered representation of the modules commonly used to create Spring web applications.

_Figure 1-2. The Spring Web Stack(those with dotted lines will not be covered in this study guide)_

This study guide focuses on helping developers understand how Spring's web infrastructure is designed, and how to write Spring web applications in a few easy steps by maximizing Spring's potential.The study guide's objective are as follows:
- Use Spring to develop web applications
- Use Spring Web Flow to implement stateful interactions
- Use Spring Security to secure web applicatons
- Use Spring Test and other test frameworks(JUnit, JMock) to test web applications
- Create Spring web applications using Gradle[^4]

[^4]Gradle is an automated build tool that is easy to cnfigure and use on any type of application. Its build files are written using JSON and Groovy. Gradle combines the power and flexibility of Ant with dependency management and conventions of Maven into a more effective way to build. Read more about it at https://www.gradle.org.


## Who Should Use this Study Guide
This study guide is designed to help any Spring developer become familiar and comfortable with Spring-associated technologies for web development. It can also be a big help to a developer who wants to become a **Certified Spring Web Application Developer**[^5]. That is why every topic in the official VMware Spring Web study guide is given the attention that it deserves.
You do not have to be a Certified Spring Professional to use this study guide; you just need minimal knowledge of Spring. Because this study guide has a full chapter dedicated to the Spring component, it might be possible for a non-Spring developer to use this study guide too, but the _Spring Framework Reference_ official documentation should be consulted to retrieve any missing pieces of information.
In a nutshell, this study guide was written to be used by the following audiences:
- Spring Core developers who want a taste of Spring Web
- Spring developers(Certified Spring Professionals or not) who are looking forward to becoming Certified Spring Web Application Developers
- Java developers who are curious about working with Spring technologies and want to start fast.

## About the Spring Web Certification Exam
If you are interested in becoming a **Certified Spring Web Application Developer**, the first step is to go to the VMware official learning site(http://pivotal.io/training) and search for the Spring Certification section. There you will find all the details you need regarding the official trainings, including where and when they take place. The training is four days long. There is online training available as well. After creating an account on the VMware site, you can select your desired training. After you make the payment, if you choose an online training, after about a month you will receive (through the mail) an official training kit that consists of the following:
- A paire of conference headphones(usually Logitch) to be used during training to hear your trainer talk and to ask questions.
- A professional webcam(usually Logitech) to be used during training so that your trainer and colleagues can see you, thus simulating a classroom experience.[^8]
- A Spring study guide book containing the printed version of the slides your tutor will use during training.
- A Spring study lab book containing explanations and instructions for the practical exercises you will do during taining.
- A SpringSource official flash drive containing the following:
  - A JDK installer.
  - Sources necessary for your tarining. Each study lab has s small Spring web application with missing configuration and code; the student's task is to complete it to become a working application. The same model is used in the code associated with this book.
  - An install for the most recent stable version of the Spring Tool Suite(STS). The version on the flash drive is mandatory for the course because the install sets up a local Maven repository with all the needed dependencies, and a full eclipse project configuration with the lab sources. The STS also has an internal tc Server to run the lab application.
  - An HTML or PDF version of the Spring Study Lab.
  


[^5]Keep in mind that attending a Spring Web taining course by Pivotal or at a VMware Authorized Training Certer is prerequisite to becoming a Certified Spring Web Application Developer, as stated on the official site at http://mylearn.vmware.com/mgrReg/plan.cfm?plan=31111ui=www_cert.

[^6]The Spring Framework Reference is at http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/.

[^7]Depending on the area and the training certer, this item is optional.

[^8]Depending on the area and the training certer, this item is also optional.

If you do not choose to do online training, you will not receive the headphones nor the webcam. The training kit and the rest of the materials are given to you when you arrive at the location where the training is taking place. After your training, you receive a free voucher that is required to schedule the certification exam at an approved exam center near you. Basically, this voucher or voucher code is proof that you have attended official Spring Web training.
!The exam duration is **90 minutes** and consists of **50 questions**. There are both single-anser and multiple-choice questions. The questions cover(roughly) the following topics:
- Spring overview(Spring core notions)
- MVC essentials(contifurations, beans to use, converions)
- MVC forms and views
- Webflow
- Web security
- REST

The passing score for the exam is **76%**. This means that **38** correct answers are needed to pass. Most of the questions present you with a piece of Java code or configuration and then ask you what it does, so make sure that you understand the code attached to this book and write your own beans and configurations in order to understand the framework better. The good news is that all the code in the exam can be found in the sources that you are given while attending the official training. Other questions present you with affirmations about Spring Web and require you to select the correct or the invalid ones.
If you read this book, understaand all the examples, solve the practice exercises, and then attend the official training, the recommendation is to take the certification exam as soon as possible afterward. Do not allow too much time to pass between finishing  the training and taking the exam, because we are ll human after all, and information can be forgotten. Also, _the certification vouche is only valid for a year_. You can retake the exam if you fail the first time, but it will cost you  ~$150.

## How to Use this Study Guide
This study guide follows the same path as the ofiicial Spring Web training, and focuses on the topics that are found in the certification exam; but there are a few differencess, which are mentioned from now on.
This Spring study guide covers the SpringMVC Portlets. This topic is not in the exam, but you never know when you may need them in your development career, so it is better to have an overview.
The other differences are related to the tools used for the practical examples, which are mentioned in the next sectin.

## How this Book Is Structured
This study guide has eight chapters. You might think: How is this possible--the official spring study guide has eixteen chapter, right? It is better to wrap related things together, so in this study guide you have two big chapters that cover 60% of the exam topics: Chapter 3 covers Spring MVC and Chapter 7 covers Srng Web Flow. Also, some topics that have their own dedicated chapter in the official study guide have been included in other chapters, as relevant, in this book.(For example, how to test web application. there's no need of a separate chapter just for this, as testing is main portion in the development of an applicatin.)
A list of this study guide's chapters, along with a short description, is presented in Table1-1.
_**Table 1-1.** Study Guide Chapters_

Chapter | Topic | Details
--- | --- | --
1 | Introduction | An introduction to spring history, technologies, and the tools used for practice in this study guide
2 | Spring Fundamentals | Sping core concepts, components, and configurations
3 | Spring MVC | Spring Web Framework core concepts, components, and configurations
4 | Spring Portlets | What portlets are, how they can be used, and how can spring make this easier
5 | Spring RESTful Services | Advanced Spring MVC fro REST applications
6 | Spring Web with AJAX | Advanced Spring MVC with AJAX web applications
7 | Spring Web Flow | Basic and advanced topics on working with Spring Web Flow
8 | Spring Web Socket | Basic configuration and usage of Spring Web Socket
A | Appendix | Two mock exams, answers to review questions, and other comments

## How Each Chapter Is Structured
This introdudctory chapter, the one you are reading now, covers the basics of Spring and Spring related-notions that every developer using this study guide should know: what Spring is, how it has evolved, the number of official Spring projects, the Spring Web technologies, the technologies used to build and run the practical exercises, how to register fro the exam to become a Certified spring Developer, and so on. This chapter is the exception; it is sturctured differently than the others because it is designed to prepare you for what is coming next.
All the other chapters are designed to cover a Spring module and associated technologies, which will help you build a specific type of Spring web application. Each chapter is split into a few sectins, but in a nutshell, a chapter could be split as follows:
- Basics
- Configuration
- Components
- Summary
- Quick quiz
- Practical exercise

## Conventions
   ! This symbol appears in front of paragraghs that you should pay particular attention to.
   ** This symbol appears in front of a paragraph that is an observation or an execution step that you can skip.
   ? This symbol appears in front of a question fro the user.
   ... This symbol replaces missing code that is not relevant in the example.
   **CC** This symbol appears in front of a  paragraph that describes a convertion over configuration practice in Spring, a default behavior that helps a developer reduce his or her work.
   **[_random text here_]** Text surrouned by square brackets means that the text within the brackets should be replaced by a context-related notion.

## Downloading the Code
This study guide comes with code examples and practical exercises. There will be missing pieces of code that you will have to fill in to make applications work and to test your understanding of Spring Web. It is recommened that you go over the code samples and do the exercises, as similar pieces of code and configurations will appear in the certification exam.
The following downloads are available:
- Sources code for the programming examples in the book chapters
- Sources code for the programming examples in the practice section
You can downlad these items from the Source Code area of the Apress web site(www.apress.com).


## Contacting the Author
More information on Iuliana Cosmina can be found at http://ro.likedin.com/in/iuliancosmina. She can be reached at iuliana.cosmina@gmail.com. Follow her personal  coding activity at https://github.com/uiliana.

## Recommended Development Environment
If you decide to attend the official course, you will notice that the development environment recommended in this book differs quite a lot from the one used for the course--a different  editor is recommended, and a different application server, and even a different build tool. The reason for this is to improve and expand your experience as a developer and to offer a practical development infrastructure. Motivation for each chioce is mentioned in the corresponding sections.

## Recommended Build Tools
The recommended deveopment environment should be composed of the following technologies:
**Java8**. Download and install the JDK matching your operation system from http://www.oracle.com.
!It is recommended to set the JAVA_HOME environment variable to point to the directory where Java 8 is installed(the directory in which the JDK was unpacked) and add $JAVA_HOME/bin to the general path of the system.The reason behind this is to ensure that any other development application written in Java will use this version of Java, and prevent strange incompatibility errors during development.

!Verify that the version of Java that your operation system sees is the one you just installed. Open a terminal(Command+Prompt in Windows, or any type of terminal you have installed on Mac OS or Linux) and type the following:
```shell
java -version
```
You should see something similar to this:
```shell
java version "1.8.0_40"
Java(TM) SE Runtime Environment (build 1.8.0_40)
Java HotSpot(TM) 64-Bit Server VM (build 25.25-b02, mixed mode)

**Gradel 2.x**
This sources attached to this book can be compiled and executed using the Gradle Wrapper, which is a batch script on Windows, or by using a shell script on other operating systems. When you start a Gradle build via the wrapper, Gradle is automatically downloaded and used to run the build, thus you do to need to install Gradle as stated prviously. Instructions on how to do this can be found on the public documentation at www.gradle.org/docs/current/userguide/gradle_wrapper.html.

It is a good practice to keep code and build tools separate, but this study guide uses the Wrapper to easily set up the practice environment by skipping the Gradle installation step, and also because the recommended source code editor uses the Wrapper internally.

If you decide to use Gradle outside the editor, you can download the binaries only (or, if you are more curious, you can download the full package, which contains binaries, sources, and documentaions) from the official site(https://www.gradle.org), unpack it and copy the contents somewhere on the hard drive. Create a GRADLE_HOME environment variable and point it to the location where you have unpacked Gradle. Also add $GRADLE_HOME/bin to the general path of the system.

Gradle was chosen as a build tool for the sources of this book because of the easy setup, small configuration files, flexibility in defining execution tasks, and the fact that the SpringSource team currently uses it to build all Spring projects.

!Verigy that the version of Gradle that your operation system sees is the one that you just installed. Open a terminal(Command+Prompt in Windows, any type of terminal you have installed on Mac OS or Linux) and type gradle -verion. You should see something similar to this:

The preceding text shows a configuration that any Gradle command can be executed in your terminal;Gradle was installed successfully.


**Jetty 9** is an open source web server that is free to use and easy to install; that's why it was chosen to be used in this study guide instead of the SpringSource tc Server. No need to download and install this web server, though, because there is no need to. There is a Gradle plugin called Getty that will be used to download the Jetty web server and deploy your *.war artifact on it. If you want to read more about Jetty, you can do so at http://eclipse.org/jetty/.

## Recommended IDE
The recommended IDE to use this study gide is Intellij IDEA. The reason for this is that it is the most intelligent Java IDE. IntelliJ IDEA offers outstanding framework-specific coding assistance and productivity-boosting features for Java EE. Spring also includes support for Maven and Gradle. It is the perfect choice to help you focus on learnig Spring, rather than how to use an IDE. It can be downloaed from the JetBrains official site(https://www.jetbrains.com/idea/).It is also quite light on your operating system and quite easy to use.

Because the web applications developed as practice in this study guide are deploed on Jetty, the community edition of Intellij IDEA can be used because we do not need the server plugin. Ther main disadvantage of the community edition, though, is that it does not come with the Spring plugin, which is very useful in creating Spring configurationfiles because it adds the bean namespace by default.But solving the exercises in this book won't require that, so you can still consider IDEA an option. If you are curious about the full power of this IDE, you can download the Ultimate Edition, which has a trial peroid of 30 days. And you can even try to deploy the code samples on a Tomcat instance from within IDEA. You will find a example of how to do this in the appendix.

If you are already familiar with a differenct Java editor, you can use it--as long as it supports Gradle.

## The Project Sample
Most of the code usein this study guide, except the book code modules, makes up a project named **Personal Records Manager**. This is a proof of concept application that aspires to manage the personal information of a group of people. The application is multimodular and each moduler is duplicated. The projects suffixed with **practice** are missing pieces of code and configuration, and are the ones that need  to be solved by you to test your understanding of Spring Web. The projects suffixed with **solution** are proposal resolutions for the tasks. You can see the project structure and the modules in Figure 1-3.








































