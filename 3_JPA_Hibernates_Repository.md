
# define What Is the Difference Between Hibernate and Spring Data JPA?

## Repository <Spring Data JPA>

Spring data is part of the Spring Framework work for singificantly reduce the amount of boilerplate code required to implement data.


**Spring Data JPA is a module that makes JPA easy to use.**

## Java Persistence API

The Java Persistence API provides a specification for persisting, reading, and managing data from your Java object to relational tables in the database.


## Hibernate **Framework**

Hibernate is ORM Solution.

ORM : Object relational mapping

```
SELECT * FROM user; 

mapping -----------

user.findAll();

```

programming technique to map application domain model objects to the relational database table.

Similar 


**It is an implementation of the specification called JPA.**



### example ORM

JPA는 단순히 interface일 뿐이다.

JPA 핵심이 되는 EntityManager 역시 마찬가지다.

```java
package javax.persistence;

import ...

public interface EntityManager {

    public void persist(Object entity);

    public <T> T merge(T entity);

    public void remove(Object entity);

    public <T> T find(Class<T> entityClass, Object primaryKey);

    // More interface methods...
```


https://dzone.com/articles/what-is-the-difference-between-hibernate-and-sprin-1

https://suhwan.dev/2019/02/24/jpa-vs-hibernate-vs-spring-data-jpa/

https://victorydntmd.tistory.com/195
