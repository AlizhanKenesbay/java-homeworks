# Ответы на домашние задания по разделу «Java» - урок 2

## Задача 1
#### Класс Car:
```java
public class Car {
    String brand;
    String model;
    int speed;

    public void start() {
        System.out.println("Машина бренда: " + brand + " | Марки: " + model + " | Едет со скоростью: " + speed + " км/ч");
    }

    public void stop() {
        System.out.println(brand + " остановлена");
    }
}
```
#### Класс Test:
```java
public class Test {
    public static void main(String[] args) {
        Car car1 = new Car();
        car1.brand = "BMW";
        car1.model = "X7";
        car1.speed = 200;

        Car car2 = new Car();
        car2.brand = "Audi";
        car2.model = "A8";
        car2.speed = 250;

        car1.start();
        car2.start();

        car1.stop();
        car2.stop();
    }
}
```


## Задача 2
#### Класс Person:
```java
public class Person {
    public void printName(String lastName, String firstName) {
        System.out.println("Ваше фамилия: " + lastName + ", ваше имя: " + firstName);
    }
}
```
#### Класс Test:
```java
public class Test {
    public static void main(String[] args) {
        Person person = new Person();
        String firstName = "Алексей";
        String lastName = "Петров";
        person.printName(lastName, firstName);
    }
}
```


## Задача 3
#### Класс Calculator:
```java
public class Calculator {
    public void printSum(int a, int b, int c) {
        int sum = a + b + c;
        System.out.println("Сумма трех чисел равна: " + sum);
    }
}
```
#### Класс Test:
```java
public class Test {
    public static void main(String[] args) {
        Calculator calculator = new Calculator();
        calculator.printSum(2, 5, 3);
    }
}
```

## Задача 4, 5 ,6
#### Класс Dog:
```java
public class Dog {
    int age;
    String breed;
    String type;
    String name;

    public void eat(){
        String food = "корм";
        int foodCount = 2;
        System.out.println("Собака ест " + food + " в колличестве " + foodCount + " штук");
    }

    public int sumOfTwoNumbers() {
        return 24+25;
    }

    public String getHelloWorld() {
        return "Hello World!";
    }
}
```
#### Класс Test:
```java
public class Test {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();
        System.out.println("Сумма чисел 24 и 25: " + dog.sumOfTwoNumbers());
        System.out.println(dog.getHelloWorld());
    }
}
```
