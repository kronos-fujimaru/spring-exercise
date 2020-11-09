### 演習1（解答例）

<br>

**ExRestController.java**

```java
package com.example.springexercise.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("rest-controller")
public class ExRestController {

    @GetMapping("/ex1")
    public String ex1() {
        return "Hello, Spring";
    }

}
```
