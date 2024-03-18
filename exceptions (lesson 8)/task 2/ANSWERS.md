# Ответы на домашние задания по разделу «Java» - урок 8 задача 2

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/validate-event-program)

#### Абстрактный класс Event:
```java
public abstract class Event {
    private String title;
    private int releaseYear;
    private int age;

    public Event(String title, int releaseYear, int age) {
        this.title = title;
        this.releaseYear = releaseYear;
        this.age = age;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public int getReleaseYear() {
        return releaseYear;
    }

    public void setReleaseYear(int releaseYear) {
        this.releaseYear = releaseYear;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Event{" + "title='" + title + '\'' +
                ", releaseYear='" + releaseYear + '\'' +
                ", age=" + age + '}';
    }
}
```

#### Класс Movie наследуемый от Event:
```java
public class Movie extends Event {

    public Movie(String title, int releaseYear, int age) {
        super(title, releaseYear, age);
    }
}
```

#### Класс Theatre наследуемый от Event:
```java
public class Theatre extends Event {

    public Theatre(String title, int releaseYear, int age) {
        super(title, releaseYear, age);
    }
}
```
<br>

#### Класс Main:
```java
public class Main {
    public static void main(String[] args) {
        for (Event event : getMovies()) {
            validEvent(event);
        }
        for (Event event : getTheatre()) {
            validEvent(event);
        }
        System.out.println("Все события корректны");
    }

    public static void validEvent(Event event) {
        if (event.getTitle().isBlank() || event.getAge() == 0 || event.getReleaseYear() == 0) {
            throw new RuntimeException("События заполнены некорректно");
        }
    }

    public static Movie[] getMovies() {
        return new Movie[] {
                new Movie("Начало", 2010, 16)
        };
    }

    public static Theatre[] getTheatre() {
        return new Theatre[] {
                new Theatre("Анна Каренина", 2017, 16)
        };
    }
}
```