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
The value for the properties are loaded in to a java.util.Properties instance with a id of dbProp using a functionality offered by the util namespace in the first line of the configuration, and then their values are accessed using SpEL(Spring Expression Language) syntax and injected into the dataSource bean.