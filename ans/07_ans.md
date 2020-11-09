### 演習7（解答例）

<br>

**ExController.java**

```java
package com.example.springexercise.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("controller")
public class ExController {

    @GetMapping("/ex7/{num}")
    public String ex7(@PathVariable("num") int num) {
        if (num % 2 == 0) {
            return "number/even";
        } else {
            return "number/odd";
        }
    }

}
```

<br>

**even.html**

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Random</title>
</head>
<body style="background-color:red;color:white;">
    an even page.
</body>
</html>
```

<br>

**odd.html**

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Random</title>
</head>
<body style="background-color:blue;color:white;">
    an odd page.
</body>
</html>
```
