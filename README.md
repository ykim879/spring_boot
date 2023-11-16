# Spring Boot
Spring Boot is a framework helps building micro service, light-weigh service which has own process to run, with minimum configuration.\
These are the three annotation to start spring application
1. **@EnableAutoConfiguration** configures your application with jar dependencies
2. **@ComponentScan** scans all the beans and package declarations.
3. **@SpringBootApplication** is combination of EnableAutoConfiguration and ComponentScan
all of above annotation used in same format (you can replace or include both EnableAutoConfiguration and ComponentScan with SpringBootApplication)
``` java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {
   public static void main(String[] args) {
      SpringApplication.run(DemoApplication.class, args);
   }
}
```
## REST APIs
HTTP should have following features: Suitable actions (GET, POST, PUT, DELETE, …​),Caching, Redirection and forwarding, Security (encryption and authentication). For REST APIs, you should consider these options: Backwards compatible APIs,
Evolvable APIs,
Scaleable services,
Securable services,
A spectrum of stateless to stateful services.
There are few annotations you can consier
### javax.persistence.Entity and org.springframework.data.jpa.repository.JpaRepository
javax.persistence (JPA) is an api that provides object-relational mapping by using annotations or XML to map objects into one or more tables of a database. By using annotation @Entity and extends repository with JpaRepository, you can do crud actions on database with java objects. However, the java data model should be as same as the data table you want to store
```java
@Entity
class Employee {...}
```
```java
interface EmployeeRepository extends JpaRepository<Employee, Long> {
}
```
On the above, the repository has generic which is <class type, id type>.
### org.springframework.context.annotation.Bean, org.springframework.context.annotation.Configuration, and org.springframework.boot.CommandLineRunner
Bean is the objects that form the backbone of your application. @Bean Annotation is applied on a method to specify it needs to be managed by spring context (SpringBootApplication, etc). @Configuration is a class-level annotation indicating that an object is a source of bean definitions. CommandLineRunner is an interface that beans implement (by using bean annotation) which will be run after the application context has been loaded. 
Spring Boot will automatically call the run method of all beans implementing CommandLineRunner after the application context has been loaded. By using SpringBootApplication, it will do component scanning, autoconfiguration, and property support, so you do not have to worry about it. 
```java
@Configuration
class LoadDatabase {
  @Bean
  CommandLineRunner initDatabase(EmployeeRepository repository) {

    return args -> {...}
}
```
### org.springframework.web.bind.annotation.GetMapping, PostMapping, PutMapping, DeleteMapping
Routes for each operation (@GetMapping, @PostMapping, @PutMapping and @DeleteMapping, corresponding to HTTP GET, POST, PUT, and DELETE calls)
```java
@DeleteMapping("/employees/{id}")
  void deleteEmployee(@PathVariable Long id) { ... }
```
