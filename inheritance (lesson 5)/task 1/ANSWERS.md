# Ответы на домашние задания по разделу «Java» - урок 5 задача 1

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/book-statuses)

#### Enum Класс Status:
```java
public enum Status {
    AVAILABLE,
    BORROWED,
    ARCHIVED,
    OVERDUED
}
```
<br>

#### Класс Book:
```java
public class Book {
    String title;
    Status status;

    public Book(String title) {
        this.title = title;
        this.status = Status.AVAILABLE;
    }

    public Status getStatus() {
        return status;
    }

    public void setStatus(Status status) {
        this.status = status;
    }
}
```
<br>

#### Класс BookMover:
```java
public class BookMover {
    public void moveToStatus(Book book, Status requestedStatus) {
        System.out.println("Moving status...");
    }
}
```

#### Класс FromAvailableStatusMover наследуемый от BookMover:
```java
public class FromAvailableStatusMover extends BookMover {
    @Override
    public void moveToStatus(Book book, Status requestedStatus) {
        String error = "Can not move book from status %s to %s%n";
        if (book.getStatus() != Status.AVAILABLE) {
            System.out.printf(error, book.getStatus(), requestedStatus);
            return;
        }
        switch (requestedStatus) {
            case BORROWED -> {
                book.setStatus(Status.BORROWED);
                System.out.println("Moving is completed");
            }
            case ARCHIVED -> {
                book.setStatus(Status.ARCHIVED);
                System.out.println("Moving is completed");
            }
            default -> System.out.printf(error, book.getStatus(), requestedStatus);
        }
    }
}
```

#### Класс FromBorrowedStatusMover наследуемый от BookMover:
```java
public class FromBorrowedStatusMover extends BookMover {
    @Override
    public void moveToStatus(Book book, Status requestedStatus) {
        String error = "Can not move book from status %s to %s%n";
        if (book.getStatus() != Status.BORROWED) {
            System.out.printf(error, book.getStatus(), requestedStatus);
            return;
        }
        switch (requestedStatus) {
            case AVAILABLE -> {
                book.setStatus(Status.AVAILABLE);
                System.out.println("Moving is completed");
            }
            case OVERDUED -> {
                book.setStatus(Status.OVERDUED);
                System.out.println("Moving is completed");
            }
            case ARCHIVED -> {
                book.setStatus(Status.ARCHIVED);
                System.out.println("Moving is completed");
            }
            default -> System.out.printf(error, book.getStatus(), requestedStatus);
        }
    }
}
```

#### Класс FromOverduedStatusMover наследуемый от BookMover:
```java
public class FromOverduedStatusMover extends BookMover {
    @Override
    public void moveToStatus(Book book, Status requestedStatus) {
        String error = "Can not move book from status %s to %s%n";
        if (book.getStatus() != Status.OVERDUED) {
            System.out.printf(error, book.getStatus(), requestedStatus);
            return;
        }
        switch (requestedStatus) {
            case AVAILABLE -> {
                book.setStatus(Status.AVAILABLE);
                System.out.println("Moving is completed");
            }
            case ARCHIVED -> {
                book.setStatus(Status.ARCHIVED);
                System.out.println("Moving is completed");
            }
            default -> System.out.printf(error, book.getStatus(), requestedStatus);
        }
    }
}
```

#### Класс FromArchivedStatusMover наследуемый от BookMover:
```java
public class FromArchivedStatusMover extends BookMover {
    @Override
    public void moveToStatus(Book book, Status requestedStatus) {
        String error = "Can not move book from status %s to %s%n";
        if (book.getStatus() != Status.ARCHIVED) {
            System.out.printf(error, book.getStatus(), requestedStatus);
            return;
        }
        switch (requestedStatus) {
            case AVAILABLE -> {
                book.setStatus(Status.AVAILABLE);
                System.out.println("Moving is completed");
            }
            default -> System.out.printf(error, book.getStatus(), requestedStatus);
        }
    }
}
```
<br>

#### Класс Main:
```java
public class Main {
    public static void main(String[] args) {
        Book book1 = new Book("Собачье сердце");

        BookMover availableStatusMover = new FromAvailableStatusMover();
        BookMover borrowedStatusMover = new FromBorrowedStatusMover();
        BookMover archivedStatusMover = new FromArchivedStatusMover();
        BookMover overduedStatusMover = new FromOverduedStatusMover();

        availableStatusMover.moveToStatus(book1, Status.BORROWED);
        borrowedStatusMover.moveToStatus(book1, Status.OVERDUED);
        overduedStatusMover.moveToStatus(book1, Status.ARCHIVED);
        archivedStatusMover.moveToStatus(book1, Status.AVAILABLE);
    }
}
```
