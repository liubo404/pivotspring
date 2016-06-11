### Annotations

Spring also supports configuration via annotations. The previous XML configuration can be replaced by a class annotated with @Configuration, and looks like this:

```java
  @Configuration
  @PropertySource(value = "classpath:datasource/db.properties")
  public class AppConfig{

         @Autowired
         Environment env;

         @Bean(name="personManager")
         public PersonManager getPersonManager(){
                return new PlainPersonManagerImpl(getPersonRepository());
         }

         @Bean(name="personRepository")
         public PersonRepository getPersonRepository(){
                PersonRepository repo = new PlainPersonRepository();
                repo.setDataSource(getDataSource());
                return repo;
         }

         @Bean(name="dataSource")
         public DataSource getDataSource(){
                DriverManagerDataSource dataSource = new DriverManagerDataSource();
                dataSource.setDriverClassName(env.getProperty("driverClassName"));
                dataSource.setUrl(env.getProperty("url"));
                dataSource.setUsername(env.getProperty("username"));
                dataSource.setPassword(env.getProperty("passowrd"));
                return dataSource;
         }
  }
```

All the code to save a Person instance looks like this:
```java
  @RunWith(SpringJUnit4ClassRunner.class)
  @ContextConfiguration(classes ={AppConfig.class})
  public class SecondAnnotationPersonSaveTest{
         @Autowired
         PersonManager personManager;

         @Test
         public void savePerson(){
                personManager.save(new Person("John", "Smith", "1980-04-03"));
         }
  }
```
When annotations are used, XML configuration files are no longer needed, nor namespaces. Specific annotations are used to mark configuration class(@Configuration) and to mark methods as bean definitios(@Bean); this is not covered because it is outside the scope of this book. What you need to remember is that the @Bean annotation makes sure that every thime the annotated method is called the same bean is returned. Withoud it, the method will return a newly created instance each time.

CC In the previous code example, each @Bean annotatin has the attribute name populated with a value to name the bean createdd by the method. This attribute is neither mandatory nor necessary. When it is not specified, the Spring IoC determines a name for the bean based on the method name by removing the _get_ and lowercasing the first letter of the remaining string.

