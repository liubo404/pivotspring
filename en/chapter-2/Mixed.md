### Mixed Approach

XML and annotations can be mixed. You could have the bean classes annotated with @Component(or any annotation extending @Repository for DAO repository classes, @Service for service classes, or @Controller for MVC handler classes) and one or more XML files, which define just the DataSource configuration and specifies where the beans are located. In the following code sample, the DataSource configuration is separated in another file(as shown in the "How Bean Factory Post Process Work" section) to decouple configuration for production and test environments.
```xml
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="
         http://www.springframework.org/schema/beans
         http://www.springframework.org/schema/beans/spring-beans.xsd
         http://www.springframework.org/schema/context
         http://www.springframework.org/schema/context/spring-context.xsd"

         <Context:component-scan base-package="com.book.beans"/>
         ...
 </beans>
```

In XML configuration files, bean definitions describe the way a dependency should be provided to them: using either constructors or setters. This is called *autowiring*. When using annotatins, the way a dependency shoud be provided is described using the @Autowire annotation on a constructor or setter^4. But you need to tell the Spring IoC container to look for that type of annotation, and the declareation <context:component-scan ...> does exactly that.

When using annotations, <bean> declarations are no longer needed because each bean type is annotated with @Component, or an extension of it, and the <context:component-scan ..> declaration tell the Spring IoC container to look for those types of annotations in the specific file. The process of identifying annotated bean types is called *autodiscovery*.

Thus what the following configuration element does is enable bean autowiring and autodiscovery anywhere in the classpath in packages(and subpackages) named as the value of the attribute base-package.
<context:component-scan base-package="com.book.beans"/>

The <context:..> declarations are Sprng's way of compacting the declaration of infrastructure beans named *PostProcessor, which take care of interpreting annotations into beans definitions.
- <context:annotation-config/> registers the following:
  - AutowiredAnnotationsBeanPosProcessor(support @Autowired, @Value, @Inject)
  - CommonAnnotationBeanPostProcessor(supports @Rsource, @PostConstruct, @PreDestroy)
  - PersistenceAnnotationBeanPostProcessor(supports @PersistenceUnit, @PersistenceContext)
  - RequiredAnnotationBeanPostProcessor(supports @Required)
- <context:component-scan base-package="com.book.beans"/> implicitly enables the functionality of <context:annotation-config> and adds support for more annotations (@Repository, @Service, @Controller, which are specializations of @Component, @Configuration, etc.)

If you want to extend your knowledge about this, you can always read the Spring Reference Documentation.^5 More detailed information is outside the scope of this book.