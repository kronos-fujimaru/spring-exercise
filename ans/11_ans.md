### 演習11（解答例）

<br>

**LoggingAspect.java**

```java
package com.example.springexercise.aspect;

import org.aspectj.lang.JoinPoint;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;

@Aspect
@Component
public class LoggingAspect {

    private static final Logger logger = LoggerFactory.getLogger(LoggingAspect.class);

    @Before("execution(* com.example.springexercise.controller.*.*(*))")
    public void before(JoinPoint joinPoint) {
        logger.info("start:{}", joinPoint.getSignature().toString());
    }

}
```
