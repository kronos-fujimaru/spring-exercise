# Spring Framework 演習問題

Eclipse上で Spring Starterプロジェクト「spring-exercise」を作成して課題に取り組んでください。

<br>

### 演習1

次の実行結果となるように以下のプログラムを作成してください。

- ExRestController.java（パッケージ：com.example.springexercise.controller）

#### 実行結果

ブラウザを開いて以下のURLにアクセスします。

http://localhost:8080/rest-controller/ex1

<img src="img/01_01.png" alt="実行結果" width="600">

<br><br>

<hr>

### 演習2

次の実行結果となるように以下のプログラムを作成してください。

- ExRestController.java（パッケージ：com.example.springexercise.controller）

> 既存のExRestControllerクラスにメソッドを追加してください。

#### 実行結果

ブラウザを開いて以下のURLにアクセスします。

http://localhost:8080/rest-controller/ex2

フルーツ名をリストに格納し、リストの内容を表示します。

<img src="img/02_01.png" alt="実行結果" width="600">

<br><br>

<hr>

### 演習3

次の実行結果となるように以下のプログラムを作成してください。

- ExRestController.java（パッケージ：com.example.springexercise.controller）

> 既存のExRestControllerクラスにメソッドを追加してください。

#### 実行結果

ブラウザを開いて以下のURLにアクセスします。

http://localhost:8080/rest-controller/ex3

フルーツ名と価格をマップに格納し、マップの内容を表示します。

<img src="img/03_01.png" alt="実行結果" width="600">

<br><br>

<hr>

### 演習4

次の実行結果となるように以下のプログラムを作成してください。

- ExRestController.java（パッケージ：com.example.springexercise.controller）

> 既存のExRestControllerクラスにメソッドを追加してください。

#### 実行結果

ブラウザを開いて以下のURLにアクセスします。

http://localhost:8080/rest-controller/ex4?message=SpringBoot!!

リクエストパラメータの値を表示します。

<img src="img/04_01.png" alt="実行結果" width="650">

> ヒント：@RequestParamアノテーションでリクエストパラメータを取得できます。

<br><br>

<hr>

### 演習5

次の実行結果となるように以下のプログラムを作成してください。

- ExRestController.java（パッケージ：com.example.springexercise.controller）
- Employee.java（パッケージ：com.example.springexercise.domain）　※作成済み

> 既存のExRestControllerクラスにメソッドを追加してください。

#### 実行結果

ブラウザを開いて以下のURLにアクセスします。

http://localhost:8080/rest-controller/ex5?id=101

リクエストパラメータで指定したIDで従業員情報（リスト）を検索し、ヒットした従業員の情報を表示します。

<img src="img/05_01.png" alt="実行結果" width="600">

リクエストパラメータで指定したIDに紐づく従業員情報がない場合は、その旨のメッセージを表示します。

<img src="img/05_02.png" alt="実行結果" width="600">

<br><br>

**Employee.java**

```java
package com.example.springexercise.domain;

import lombok.Data;

@Data
public class Employee {
    private int id;
    private String name;
    private String gender;
    private int age;

    public Employee(int id, String name, String gender, int age) {
        this.id = id;
        this.name = name;
        this.gender = gender;
        this.age = age;
    }
}
```

**ExRestController.java**

以下のリストが用意されているものとします。

```java
List<Employee> employees = Arrays.asList(new Employee(101, "Bob", "Male", 45),
                                         new Employee(102, "Alice", "Female", 32),
                                         new Employee(103, "John", "Male", 28),
                                         new Employee(104, "Gonzalez", "Male", 27),
                                         new Employee(105, "Paula", "Female", 36),
                                         new Employee(106, "Watson", "Male", 56),
                                         new Employee(107, "Eliza", "Female", 23),
                                         new Employee(108, "Duke", "-", 25));
```
