### Lifecycle and Instantiation
The beans are created in order of dependency. If a bean of type B, needs a bean of type A for its creation, the Spring container will know how to first create bean A and then inject it into bean B. If an application has multiple configuration files, the Spring container first reads all of them, internally creates a dependency tree of bean definitions, and then starts traversing the tree, starting with its lowest level where the simplest bean definitions are. In the cases mentioned in previous sections, the order for bean creation(instantiation) is dataSource, personRepository, and personManager. The steps are described in Figure2-4.
[img f24.png]

A bean cannot be created if its required dependencies do not exist; an exception is thrown in case of  missing dependencies. But how deos the Spring container know which dependencies are required? There are a few ways. One is the type of injection. spring supports two types of injection: via constructor and via setter. The constructor injection is when the constructor of a bean is defined as having an argument of type another bean. In the prvious example, the PersonManagerImpl constructor definition requires a PersonRepository instance as an argument, and thus the PersonManagerImpl requires a bean of type PersonRepository to be created before its creation.
```xml
  <!- Constructor injection ->
  <bean id="personManager" class="com.book.PersonManagerImpl">
        <constructor-arg ref="personRepository" />
  </bean>
  <!- Setter injection->
  <bean id="personRepository" class="com.book.JdbcPersonRepository">
        <property name="dataSource" ref="dataSource"/>
  </bean>
```

Any object that has a constructor with arguments cannot be constructed without passing in arguments. This restriction does not apply for the setter injection, but it can be enforced in two ways:
- By annotating the setter method with @Required. If the property is not set, a BeanInitializationException is thrown.
- By annotating the setter method with @Autowire the Spring IoC container tries to inject a bean with the specific type. If such a bean is not found, a BeanCreationException is thrown.

One of the advantages of using the setter inject is that you can create hierarchical beans, and setters will be inherited. In a setter injection, bean creation and dependency injection are two  separate steps; for constructor injection there is only one step. So basically, setter injection makes your configuration more flexible.