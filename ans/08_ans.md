### 演習8（解答例）

<br>

**ExController.java**

```java
package com.example.springexercise.controller;

import java.util.Arrays;
import java.util.List;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;

import com.example.springexercise.domain.Employee;

@Controller
@RequestMapping("controller")
public class ExController {

    （中略）

    @GetMapping("/ex8")
    public String ex8(Model model) {
        List<Employee> employees = Arrays.asList(new Employee(101, "Bob", "Male", 45),
                                                 new Employee(102, "Alice", "Female", 32),
                                                 new Employee(103, "John", "Male", 28),
                                                 new Employee(104, "Gonzalez", "Male", 27),
                                                 new Employee(105, "Paula", "Female", 36),
                                                 new Employee(106, "Watson", "Male", 56),
                                                 new Employee(107, "Eliza", "Female", 23),
                                                 new Employee(108, "Duke", "-", 25));

        model.addAttribute("employees", employees);
        return "ex8/employee";
    }

}
```

<br>

**employee.html**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
<meta charset="UTF-8">
<title>Employee</title>
</head>
<body>
    <h2>従業員情報</h2>
    <table border="1">
        <tr><th>ID</th><th>氏名</th><th>性別</th><th>年齢</th></tr>
        <tr th:each="employee : ${employees}">
            <td th:text="${employee.id}"></td>
            <td th:text="${employee.name}"></td>
            <td th:text="${employee.gender}"></td>
            <td th:text="${employee.age}"></td>
        </tr>
    </table>
</body>
</html>
```
