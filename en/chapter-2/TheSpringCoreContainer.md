## The Spring Core Container
The Spring core container is made of the following modules:
- spring-beans
- spring-core
- spring-context and spring-context-support (provides support classes that help integration of third-party libraries for caching, mailing, scheduling, and template engines)
- spring-expression

The spring-core and spring-beans modules provided the fundamental part of the framework: the Ioc and dependency injection features, which the conatiner needs to solve and inject dependencies as specified in the configuration. The sprng-context module extends the provious two modules, adding support for integrationalization, resource loading, event propagation, and transparent creation of contexts. The core component of this module is the ApplicatioContext interface. The spring-expression module provided a powerful Expression Language for querying and manipulating an object graph at runtime, and for operations like setting and getting property values, property assignment, and others.

Considering the diagram in Figure 2-1, the classes needed to support implementaing the operation to save a Person instance look like tis:
```java
public class PlainPersonManagerImpl implements PersonManager{
       PersonRepository repo;
       //injecting a dependency using the custructor
       public PlainPersonManagerImpl(PersonRepository repo){
       	      this.repo = repo;
       }
       ...
}

public class PlainPersonRepository implements PersonRepository{
       private DataSource dataSource;
       @Override
       private int save(Person person){
       	       ...
	}
	//injecting a dependency using a setter method
	public void setDataSource(DataSource dataSource){
	       this.dataSource = dataSource;
        }
}

```

! The PlainPersonRepository class is a simple POJO persistence handler. Its sole responsibility is to ensure Person instances are saved and retrieved from the database. Its behavior is built on a javax.sql.DataSource implementation. This is different from the Spring Data JPA repositories used in the Personal Records Manager project, which will be presented later. The approach specific to this chapter is Spring Core-based, which is more "old-style", before Spring Data JPA existed; this is to best introduce the Spring core modules and possibilities.

To implement that functionality in plain Java language, you have to write something like this:
```java
PersonRepository repo = new PlainPersonRepository();
DataSource datasource = new com.oracle.jdbc.pool.OracleDataSource();
dataSource.setUrl("jdbc:oracle:thin:@localhost:1521:orcl");
//set other dataSource properties
...
repo.setDataSource(dataSource);
PersonManager personManager = new PlainPersonManagerImpl(repo);
Person person = new Person("John", "Smith", "1980-04-13");
//Use the manager
personManager.save(person);
```

As you can easily see, except the last line, everything else is setup code--the preparation before the execution of the method. It is a lot of code. What would happen if you decided to change method signatures or to use a different DataSource implementation? A big part of this code would have to be changed too.
In the next section, let's see how Spring does the same thing.
