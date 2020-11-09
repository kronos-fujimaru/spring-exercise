### 演習4（解答例）

<br>

**ExRestController.java**

```java
package com.example.springexercise.controller;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("rest-controller")
public class ExRestController {

    （中略）

    @GetMapping("/ex4")
    public String ex4(@RequestParam("message") String message) {
        return message;
    }

}
```
