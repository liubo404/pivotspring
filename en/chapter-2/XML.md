### XML
The following code is the XML content of a file named app-simple-config.xml, which is the configuration file for a simple Spring application:
```xml
<beans>
	<bean id="personManager" class="com.book.plain.PlainPersonManagerImpl">
	      <constructor-arg ref="personRepository" />
	</bean>
	<bean id="personReposity" class="com.book.plain.PlainPersonRepository">
	      <property name="dataSource" ref="dataSource" />
	</bean>
	<bean id="dataSource" class="com.oracle.jdbc.pool.OracleDataSource">
	      <property name="URL" value="jdbc:oracle:thin:@localhost:1521:orcl" />
	</bean>
</beans>
```
And here is how the code to save a Person instance looks with Spring:
```java
//Create the application from the configuration
ApplicatonContext context = new ClassPathXmlApplicationContext("app-simple-config.xml");
//Look up the application manager interface
PersonManager manager = (PersonManager) context.getBean("personManager");
//Use the manager
manager.sava(new Person("John", "Smith", "1980-04-13"));
```

As you can see, the code is alot smaller, because all the preparation of the environment was move into the XML configuration file. And the configuration file can be manipulated more easily. If an external property file is used as entry for some of the values in it, in some simple cases, the application doesn't even have to be recompiled to change behavior. The DataSource configuration can be separated from the general configuration file, which can later allow you to easigy switch between DataSource implementations--depending on the context in which a code should run.

```xml
<uti:properties id="dbProp" location="classpath:datasource/db.properties"/>

<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
<property name="driverClassName" value="#{dbProp.driverClassName}"/>
<property name="url" value="#{dbProp.url}"/>
<property name="username" value="#{dbProp.username}"/>
<property name="password" value="#{dbProp.password}"/>
<bean>
```

In the previous example, the property values that look like #{value} are loaded from the db.properties file, which contains the following:
```
driverClassName=org.h2.Driver
url=jdbc:h2:~/prod
username=prod
password=prod
```
The value for the properties are loaded in to a java.util.Properties instance with a id of dbProp using a functionality offered by the util namespace in the first line of the configuration, and then their values are accessed using SpEL(Spring Expression Language) syntax and injected into the dataSource bean.(There is another way to do this using a component named PropertyPlaceholderConfigurer, which is covered in the "How Bean Factory Post Processors Work" section.)Spring knows how to do this because configuration files are constructured using XML namespaces.

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:util="http://www.springframework.org/schema/util"
       xsi:schemaLocation="
       http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/util
       http://www.springframework.org/schema/spring-util.xsd">
       ...
</beans>
```

The underlined values in the previous example show how a prefix is assigned to a namespace and how a namespace is associated with an XSD schema that contains the XML elements thant can be used in the configuration file. Ususally, each namespace contains definitions for all XML tags for a specific spring module, or a group of tags with related responsibilities.

As everythis in Spring is a bean, most commonly used configuration styles use the bean's root element, and the namespace for it is declared using the xmlns attribute. When additional namespaces are used, the elments defined by them need to be used inside the current elments(beans). They need to have a prefix associated so that the Spring IoC knows in which namesace to look for those element definitions; notations such as xmlns:[prefix]="[namespace URL]" are used.

! The running code in this example can be found in 02-chapter-solution project. This is a module of the book-code project, which was designed to gradually test your knowledge acquired while reading this book. The book-code contains one or more modules fro eache chapter. Some module names are postfixed with -practice and contain a series of TODO tasks that the developer should be able to complete after reading a chapter.

Ther modules prefixed with -solution contain the completed tasks and are meant to e used for comparison with the developer's own solution. Sometimes a solution module might contain extra code that is meant simply to show the developer other situations that he might encounter in Spring projects.

Fox example, by splitting up the configuration file to isolate the DataSource configuration, you could have the following configuration for a production environment:
```java
ApplicationContext context = new ClassPathXmlApplicationContext("application-config.xml", "db-config.xml");

```
And this configuration could be for a test environment:
```java
ApplicationContext context = new ClassPathXmlApplicatonContext("application-config.xml","test-db-config.xml");
```

The two environments are completely decoupled, and the tests are very easy to write. Figure 2-3 displays a typical structure for a Spring Maven project with a split configuration for production and a test environment.


! In this example, the configuration files were created under a directory named spring to emphasize that these are Spring configuration files, because in a more complex project there could be XML configuration files for other purpose(for example, logging or caching stored outside of the spring directory). The code in this book intentionally skips the spring directory from the path to reduce the size of the quotes and to make the list of configuration files more readable.

In the configuraton files, and when instantiating contexts, resources are usually prefixed with a word that tells the Spring container where they are located. These prefixes can be used for any type of resources needed in an application. Consider a standard Mavensetup for a project like the one in Figure 2-3, Table 2-1 shows the paths where a Spring container would look for resource files depending on the prefix.

_Table 2-1. Prefixes and Corresponding Paths_

Prefix | Location | Comment
---|---|---
no prefix|In root directory where the class creating the context is executed.|In the main or test directory. The type of the resouce being loaded depends on the ApplicationContext instance being used.(A detailed example is presented after this table.)
classpath:|The resourceshould be obtained from the classpath.|In the resources directory; the resource is of type ClassPathResource.
file:|In the absolute location following the prefix.|The resource is loaded as a URL from the filesystem and is of type UrlResource.
http:|In the web location following the prefix.|The resource is loaded as a URL and is of type UrlResource.

Thw following is an example of resource loadfing without using a prefix:
```java
Resource template = ctx.getResource("application-config.xml");
```

Depending on  the context class used, the resouce loaded can have one of the following types:
- If ctx is ClassPathXmlApplicationContext instance, the resource type is ClassPathResouce
- If ctx is a FileSystemXmlApplicationContext instance, the resouce type is FileSystemResource
- If ctx is a WebApplicationContext instance, the resource type is ServletContextResource