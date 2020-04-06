
## @SpringBootApplication

@SpringBootApplication is functions like the following things

>  @ComponentScan @EnableAutoConfiguration @Configuration


### @ComponentScan 
> Find annotations such as @Repository @Configuration @Service ..etc and Register the bean created by each.

### @EnableAutoConfiguration
> The role of automatically registering Spring beans that are frequently used in the Spring FrameWork in the container

> It has bean of ServletWebServerFactory.


### @Configuration
> It tell us This File is Spring's configuration related


## Custom AutoConfiguration

### using resources.META-INF spring.factories / project A ---->  project B

#### in A

in my case

```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
me.bysu.demo.HoloConfiguration
```

Add @ConditionalOnMissingBean in Configuration.class, It make Holoman bean edit in B.

### in B

just use bean to define at A


#### 1 case , edit bean that was defined in A

just make new bean, @ConditionalOnMissingBean in A make it work

```java
    @Bean
    public Holoman holoman(){
        Holoman holoman = new Holoman();
        holoman.setName("tmp2");
        holoman.setHowLong(40);
        return holoman;
    }
```

#### 2 case , edit bean that was defined in A

in B
``` 
    holoman.name = tmp3
    holoman.how-long = 10
```

in A

make Properties class

```java
@ConfigurationProperties("holoman")
public class HolomanProperties {

    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getHowLong() {
        return howLong;
    }

    public void setHowLong(int howLong) {
        this.howLong = howLong;
    }

    private int howLong;
}
```

make configuration class

```java 
@Configuration
@EnableConfigurationProperties(HolomanProperties.class)
public class HoloConfiguration {
    @Bean
    @ConditionalOnMissingBean
    public Holoman holoman(HolomanProperties properties){
        Holoman holoman = new Holoman();
        holoman.setHowLong(properties.getHowLong());
        holoman.setName(properties.getName());
        return holoman;
    }
}
```
