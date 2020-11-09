### 演習2（解答例）

<br>

**ExRestController.java**

```java
package com.example.springexercise.controller;

import java.util.ArrayList;
import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("rest-controller")
public class ExRestController {

    （中略）

    @GetMapping("/ex2")
    public List<String> ex2() {
        List<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        return fruits;
    }

}
```
