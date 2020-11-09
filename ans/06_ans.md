### 演習6（解答例）

<br>

**ExRestController.java**

```java
package com.example.springexercise.controller;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import com.example.springexercise.domain.Employee;

@RestController
@RequestMapping("rest-controller")
public class ExRestController {

    （中略）

    @GetMapping("/ex6/{id}")
    public String ex6(@PathVariable("id") int id) {
        List<Employee> employees = Arrays.asList(new Employee(101, "Bob", "Male", 45),
                                                 new Employee(102, "Alice", "Female", 32),
                                                 new Employee(103, "John", "Male", 28),
                                                 new Employee(104, "Gonzalez", "Male", 27),
                                                 new Employee(105, "Paula", "Female", 36),
                                                 new Employee(106, "Watson", "Male", 56),
                                                 new Employee(107, "Eliza", "Female", 23),
                                                 new Employee(108, "Duke", "-", 25));

        for (Employee employee : employees) {
            if (id == employee.getId()) {
                return "ID:" + employee.getId() + "<br>Name:" + employee.getName() +
                        "<br>Genger:" + employee.getGender() + "<br>Age:" + employee.getAge();
            }
        }

        return "Employee could not be found.";
    }

}
```
