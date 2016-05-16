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