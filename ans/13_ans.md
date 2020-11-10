### 演習13（解答例）

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
    <div th:if="${books} and ${#lists.isEmpty(books)}">
        <hr>
        条件に一致する書籍が見つかりません。
    </div>
    <div th:if="!${#lists.isEmpty(books)}">
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
