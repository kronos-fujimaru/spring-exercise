### 演習5（解答例）

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
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import com.example.springexercise.domain.Employee;

@RestController
@RequestMapping("rest-controller")
public class ExRestController {

    （中略）

    @GetMapping("/ex5")
    public String ex5(@RequestParam("id") int id) {
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

<br>

**Employee.java**

```java
package com.example.springexercise.domain;

import lombok.Data;

@Data
public class Employee {
    private int id;          // 従業員ID
    private String name;     // 氏名
    private String gender;   // 性別
    private int age;         // 年齢

    public Employee(int id, String name, String gender, int age) {
        this.id = id;
        this.name = name;
        this.gender = gender;
        this.age = age;
    }
}
```
