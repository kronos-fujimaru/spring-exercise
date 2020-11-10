### 演習12（解答例）

<br>

**BookForm.java**

```java
package com.example.springexercise.form;

import lombok.Data;

@Data
public class BookForm {
    private int price;
}
```

<br>

**BookService.java**

```java
package com.example.springexercise.service;

import java.util.List;

import com.example.springexercise.domain.Book;

public interface BookService {
    List<Book> findByPrice(int price);
}
```

<br>

**BookServiceImpl.java**

```java
package com.example.springexercise.service;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

import org.springframework.stereotype.Service;

import com.example.springexercise.domain.Book;

@Service
public class BookServiceImpl implements BookService {

    @Override
    public List<Book> findByPrice(int price) {
        List<Book> books = Arrays.asList(new Book(1, "Java Book - Basic", 3500),
                new Book(2, "Java Book - Advanced", 5000),
                new Book(3, "PHP Book - Basic", 1000),
                new Book(4, "PHP Book - Advanced", 2000),
                new Book(5, "SQL Book", 1500),
                new Book(6, "JavaScript Book", 4000),
                new Book(7, "HTML/CSS Book", 3000),
                new Book(8, "Spring Framework Book", 10000));

        List<Book> result = new ArrayList<>();

        for (Book book : books) {
            if (book.getPrice() <= price) {
                result.add(book);
            }
        }

        return result;
    }

}
```

<br>

**BookController.java**

```java
package com.example.springexercise.controller;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.validation.BindingResult;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

import com.example.springexercise.domain.Book;
import com.example.springexercise.form.BookForm;
import com.example.springexercise.service.BookService;

@Controller
@RequestMapping("books")
public class BookController {

    @Autowired
    private BookService service;

    @GetMapping
    public String index(Model model) {
        BookForm bookForm = new BookForm();
        model.addAttribute(bookForm);
        return "book/index";
    }

    @GetMapping("/search")
    public String search(@Validated BookForm bookForm, BindingResult bindingResult, Model model) {
        List<Book> books = service.findByPrice(bookForm.getPrice());

        model.addAttribute("books", books);
        model.addAttribute(bookForm);
        return "book/index";
    }

}
```

<br>

**index.html**

```java
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
<meta charset="UTF-8">
<title>Book</title>
</head>
<body>
    <h2>書籍検索</h2>
    <table>
        <tr th:if="${errorList}" th:each="error : ${errorList}">
            <td style="color:red;" th:text="${error}"></td>
        </tr>
    </table>
    <form th:action="@{/books/search}" method="get" th:object="${bookForm}">
        価格 ≦ <input type="number" id="price" name="price" min="0" max="100000" value="0" th:field="*{price}" style="text-align:right;" required>
        <button type="submit">検索</button>
    </form>
    <div th:if="${books}">
        <hr>
        <table border="1">
            <tr><th>ID</th><th>タイトル</th><th>価格</th></tr>
            <tr th:each="book : ${books}">
                <td th:text="${book.id}"></td>
                <td th:text="${book.title}"></td>
                <td th:text="${book.price + '円'}"></td>
            </tr>
        </table>
    </div>
</body>
</html>
```
