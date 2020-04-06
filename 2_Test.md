# Test


## Add dependency spring-boot-test
You can use below when add boot-test

### Junit

### Mockito

#### Basic setting

```java
@RunWith (SpringRunner.calss)

@SpringBootTest
```


#### (webEnvironment = SpringBootTest.WebEnvironment.MOCK) is default value

It make mocking servlet replace nomal servlet

##### MockMvc

add
```java
 @AutoConfigureMockMvc

public lass ~~
```

```java
@AUtowired
MockMvc mockMVc

```

#### (webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)

```java
@Autowired 
TestRestTemplate testRestTemplate

String result = testRestTemplate.getForObject("/", String.calss);

assertThant(result).issEqualTo(~~)
``` 

It work real, but It too big and heavy, so many case we use MookBean

##### MookBean

```java
@MockBean
RegisteredBean itIsFakeObj

when(itIsFakeObj.getName()).thenReturn("Like RegisterdBean Work");

```


##### Async

need to add dependency about spring webflux

```java
 @Autowired
 WebTestClient webTestClient;

 webTestClient.get().uri("/url").exchange()
    .expectStatus().isOk()
    .expectBody(String.class).isEqualTo("str~");
 ```


##  JsonTest

```java
@RunWith (SpringRunner.calss)

@JsonTest

@Autowired
JacksonTester<Sample>
```
