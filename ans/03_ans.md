### 演習3（解答例）

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
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("rest-controller")
public class ExRestController {

    （中略）

    @GetMapping("/ex3")
    public Map<String, Integer> ex3() {
        Map<String, Integer> fruits = new HashMap<>();
        fruits.put("Apple", 100);
        fruits.put("Banana", 200);
        fruits.put("Cherry", 300);
        return fruits;
    }

}
```
