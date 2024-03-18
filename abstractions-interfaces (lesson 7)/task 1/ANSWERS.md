# Ответы на домашние задания по разделу «Java» - урок 7 задача 1

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/library-users-project)

#### Интерфейс Reader:
```java
public interface Reader {
    void borrowBook();
    void returnBorrowedBook();
    String getName();
}
```

#### Интерфейс Librarian:
```java
public interface Librarian {
    void orderBook(Supplier supplier, String bookTitle);
}
```

#### Интерфейс Administrator:
```java
public interface Administrator {
    void issueBook(Reader reader, String bookTitle);
    void overdueNotification(Reader reader, String bookTitle);
}
```

#### Интерфейс Supplier наследуемый от интерфейса Reader:
```java
public interface Supplier extends Reader {
    void deliverBook(String bookTitle);
    String getName();
}
```
<br>

#### Класс User имплементирующий интерфейсы Reader, Librarian, Administrator:
```java
public class User implements Reader, Librarian, Administrator {
    private String name;

    public User(String name) {
        this.name = name;
    }

    @Override
    public void borrowBook() {
        System.out.println(getName() + " взял книгу");
    }

    @Override
    public void returnBorrowedBook() {
        System.out.println(getName() + " вернул книгу");
    }

    @Override
    public void orderBook(Supplier supplier, String bookTitle) {
        System.out.println(getName() + " заказал у " + supplier.getName() + " книгу " + bookTitle);
    }

    @Override
    public void issueBook(Reader reader, String bookTitle) {
        System.out.println(getName() + " выдал книгу '" + bookTitle + "' для " + reader.getName());
    }

    @Override
    public void overdueNotification(Reader reader, String bookTitle) {
        System.out.println(getName() + " уведомил о просрочке книги '" + bookTitle + "' для " + reader.getName());
    }

    public String getName() {
        return name;
    }
}
```
<br>

#### Класс BookSupplier имплементирующий интерфейс Supplier:
```java
public class BookSupplier implements Supplier {
    private String name;

    public BookSupplier(String name) {
        this.name = name;
    }

    @Override
    public void borrowBook() {
        System.out.println(getName() + " взял книгу");
    }

    @Override
    public void returnBorrowedBook() {
        System.out.println(getName() + " вернул книгу");
    }

    @Override
    public void deliverBook(String bookTitle) {
        System.out.println(getName() + " доставил книгу '" + bookTitle + "' ");
    }

    @Override
    public String getName() {
        return name;
    }
}
```
<br>

#### Класс Main:
```java
public class Main {
    public static void main(String[] args) {
        User reader = new User("Читатель Андрей");
        User admin = new User("Администратор Михаил");
        User librarian = new User("Библиотекарь Вася");
        BookSupplier supplier = new BookSupplier("Поставщик Петя");

        admin.issueBook(reader, "Анна Каренина");
        admin.overdueNotification(reader, "Анна Каренина");
        System.out.println();

        librarian.orderBook(supplier, "Игра Престолов");
        supplier.deliverBook("Игра Престолов");
        System.out.println();

        librarian.issueBook(supplier, "Кровь пот и пиксели");
        supplier.returnBorrowedBook();
    }
}
```
