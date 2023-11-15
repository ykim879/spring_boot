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
## Rest
