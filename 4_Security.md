# Security

from : https://spring.io/guides/topicals/spring-security-architecture   

authentication (who are you?) and authorization (what are you allowed to do?)   

## Authentication = access control

Authentication

```java
public interface AuthenticationManager {

  Authentication authenticate(Authentication authentication)
    throws AuthenticationException;
}
```
3 case of return   
> Authentication  : if it can verify that the input represents a valid principal.   
> AuthenticationException  : if it believes that the input represents an invalid principal. - 401 Error   
> null : it can’t decide.


![img](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/authentication.png)   


Often, each of those is a ProviderManager, and they share a parent. The parent is then a kind of "global" resource, acting as a fallback for all providers.

## Web Security

pring Security in the web tier (for UIs and HTTP back ends) is based on Servlet Filters

![img](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/filters.png)   

Spring Security is installed as a single Filter in the chain, and its concrete type is FilterChainProxy

![img](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/security-filters.png)   

![img](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/security-filters-dispatch.png)   

