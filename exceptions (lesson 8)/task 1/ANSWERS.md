# Ответы на домашние задания по разделу «Java» - урок 8 задача 1

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/user-access-checking-program)

#### Класс-исключение AccessDeniedException:
```java
public class AccessDeniedException extends Exception {
    public AccessDeniedException(String message) {
        super(message);
    }
}
```

#### Класс-исключение UserNotFoundException:
```java
public class UserNotFoundException extends Exception {
    public UserNotFoundException(String message) {
        super(message);
    }
}
```
<br>

#### Класс User:
```java
public class User {
    private String login;
    private String password;
    private String email;
    private int age;

    public User(String login, String password, String email, int age) {
        this.login = login;
        this.password = password;
        this.email = email;
        this.age = age;
    }

    public String getLogin() {
        return login;
    }

    public void setLogin(String login) {
        this.login = login;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```
<br>

#### Класс Main:
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Введите логин: ");
        String login = scanner.nextLine();
        System.out.print("Введите пароль: ");
        String password = scanner.nextLine();

        try {
            User user = getUserByLoginAndPassword(login, password);

            validateUser(user);

            System.out.println("Доступ предоставлен");
        } catch (Exception e) {
            System.out.println("Доступ не может быть предоставлен " + e.getMessage());
        }

    }

    public static User[] getUsers() {
        User user1 = new User("john", "pass", "john@gmail.com", 24);
        User user2 = new User("bob", "12354af1","bob@gmail.com",  18);
        User user3 = new User("mark", "987611","mark@gmail.com",  16);

        return new User[]{user1, user2, user3};
    }

    public static User getUserByLoginAndPassword(String login, String password) throws UserNotFoundException {
        User[] users = getUsers();
        for (User user : users) {
            if (user.getLogin().equalsIgnoreCase(login) && user.getPassword().equalsIgnoreCase(password)) {
                return user;
            }
        }
        throw new UserNotFoundException("User not found");
    }

    public static void validateUser(User user) throws AccessDeniedException {
        if (user.getAge() < 18) {
            throw new AccessDeniedException("User is under 18");
        }
    }
}
```