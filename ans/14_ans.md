### 演習14（解答例）

<br>

**LoginForm.java**

```java
package com.example.springexercise.form;

import javax.validation.constraints.NotEmpty;

import lombok.Data;

@Data
public class LoginForm {
    @NotEmpty(message = "ログインIDを入力してください。")
    private String loginId;

    @NotEmpty(message = "パスワードを入力してください。")
    private String password;
}
```

<br>

**LoginService.java**

```java
package com.example.springexercise.service;

import com.example.springexercise.domain.User;

public interface LoginService {
    User login(String userId, String password);
}
```

<br>

**LoginServiceImpl.java**

```java
package com.example.springexercise.service;

import java.util.Arrays;
import java.util.List;

import org.springframework.stereotype.Service;

import com.example.springexercise.domain.User;

@Service
public class LoginServiceImpl implements LoginService {

    @Override
    public User login(String userId, String password) {
        List<User> users = Arrays.asList(new User("Taro Yamada", "user01@example.com", "pass01"),
                                        new User("Hanako Sato", "user02@example.com", "pass02"),
                                        new User("Ichiro Suzuki", "user03@example.com", "pass03"));

        for (User user : users) {
            if (user.getUserId().equals(userId) && user.getPassword().equals(password)) {
                return user;
            }
        }

        return null;
    }

}
```

<br>

**LoginController.java**

```java
package com.example.springexercise.controller;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

import javax.servlet.http.HttpSession;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.validation.BindingResult;
import org.springframework.validation.ObjectError;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.servlet.mvc.support.RedirectAttributes;

import com.example.springexercise.domain.User;
import com.example.springexercise.form.LoginForm;
import com.example.springexercise.service.LoginService;

@Controller
@RequestMapping("login")
public class LoginController {

    @Autowired
    private LoginService service;

    @Autowired
    private HttpSession session;

    @GetMapping
    public String show(Model model) {
        LoginForm userForm = new LoginForm();
        model.addAttribute(userForm);
        return "login";
    }

    @PostMapping
    public String login(@Validated LoginForm userForm, BindingResult bindingResult,
                        RedirectAttributes redirectAttributes, Model model) {
        if (bindingResult.hasErrors()) {
            System.out.println("test");
            List<String> errorList = new ArrayList<>();

            for (ObjectError error : bindingResult.getAllErrors()) {
                errorList.add(error.getDefaultMessage());
            }

            redirectAttributes.addFlashAttribute("errorList", errorList);
            model.addAttribute(userForm);
            return "redirect:/login";
        } else {
            User user = service.login(userForm.getLoginId(), userForm.getPassword());

            if (user != null) {
                session.setAttribute("user", user);
                return "redirect:/menu";
            } else {
                redirectAttributes.addFlashAttribute("errorList", Arrays.asList("ログインIDまたはパスワードが正しくありません。"));
                model.addAttribute(userForm);
                return "redirect:/login";
            }
        }
    }

}
```

<br>

**login.html**

```java
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
<meta charset="UTF-8">
<title>Login</title>
</head>
<body>
    <h2>ログイン画面</h2>
    <form th:action="@{/login}" method="post" th:object="${loginForm}">
        ログインID:<input type="text" id="loginId" name="loginId" th:field="*{loginId}"><br>
        パスワード:<input type="password" id="password" name="password" th:field="*{password}"><br>
        <button type="submit">ログイン</button>
    </form>
    <br>
    <table>
        <tr th:if="${errorList}" th:each="error : ${errorList}">
            <td style="color:red;" th:text="${error}"></td>
        </tr>
    </table>
</body>
</html>
```
