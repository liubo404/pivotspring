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