### 演習15（解答例）

<br>

**menu.html**

```java
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
<meta charset="UTF-8">
<title>Menu</title>
</head>
<body>
    <h2>メニュー画面</h2>
    <div>
        こんにちは、<span th:text="${session.user.userName}"></span>さん
        &emsp;<a th:href="@{/logout}">ログアウト</a>
    </div>
    <ul>
        <li><a href="https://www.google.com/" target="_blank">Google</a></li>
        <li><a href="https://www.apple.com/jp/" target="_blank">Apple</a></li>
        <li><a href="https://ja-jp.facebook.com/" target="_blank">Facebook</a></li>
        <li><a href="https://www.amazon.co.jp/" target="_blank">Amazon</a></li>
    </ul>
    <br>
</body>
</html>
```

<br>

**LogoutController.java**

```java
package com.example.springexercise.controller;

import javax.servlet.http.HttpSession;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("logout")
public class LogoutController {

    @Autowired
    private HttpSession session;

    @GetMapping
    public String logout() {
        session.invalidate();
        return "redirect:/login";
    }

}
```
