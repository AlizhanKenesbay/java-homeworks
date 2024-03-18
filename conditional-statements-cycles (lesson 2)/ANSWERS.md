# Ответы на домашние задания по разделу «Java» - урок 2
```java
import java.util.Scanner;

public class RuntimeHomework {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Задача 1: Четные числа от 1 до 10");
        for (int i = 1; i < 10; i++) {
            if (i % 2 == 0) {
                System.out.println(i);
            }
        }

        System.out.println("Задача 2: Вывести на экран таблицу умножения на 3");
        int numberMultiplier = 3;
        for (int i = 0; i < 10; i++) {
            int result = numberMultiplier * i;
            System.out.printf("%d * %d = %d%n",numberMultiplier, i, result);
        }


        System.out.println("Задача 3: Проверка на простое число");
        System.out.print("Введите число для проверки на его простоту: ");
        int number = scanner.nextInt();
        boolean primeNumberCheck = true;
        for(int i = 2; i < number; i++) {
            if (number % i == 0) {
                primeNumberCheck = false;
            } else {
                primeNumberCheck = true;
            }
        }

        if (primeNumberCheck) {
            System.out.println("Число простое");
        } else {
            System.out.println("Число не является простым");
        }


        System.out.println("Задача 4: Факториал числа");
        System.out.print("Введите число: ");
        int num = scanner.nextInt();
        long result = 1;

        for (int i = 1; i <= num; i++) {
            result *= i;
        }
        System.out.printf("%d! = %d%n", num, result);


        System.out.println("Задача 5: Сумма чисел от 1 до 100, которые делятся на 3");
        int sum = 0;
        for (int i = 1; i < 101; i++) {
            if (i % 3 == 0) {
                sum += i;
            }
        }
        System.out.println("Сумма всех чисел от 1 до 100, которые делятся на 3: " + sum);


        System.out.println("Задача 6: Простой калькулятор");
        System.out.print("Введите первое число: ");
        int number1 = scanner.nextInt();
        System.out.print("Введите второе число: ");
        int number2 = scanner.nextInt();
        System.out.print("Введите операцию (+, -, *, /): ");
        char operation = scanner.next().charAt(0);

        int calculatorResult = 0;

        switch (operation) {
            case '+' -> calculatorResult = number1 + number2;
            case '-' -> calculatorResult = number1 - number2;
            case '*' -> calculatorResult = number1 * number2;
            case '/' -> calculatorResult = number1 / number2;
            default -> System.out.println("Неправильная операция");
        };

        System.out.printf("%d %c %d = %d%n", number1, operation, number2, calculatorResult);


        System.out.println("Задача 7: Високосный год");
        System.out.println("Введите год в формате \"yyyy\" ");
        int year = scanner.nextInt();
        if ((year % 4 == 0) && ((year % 100 != 0) || (year % 400 == 0))) {
            System.out.println("Количество дней 366");
        } else {
            System.out.println("Количество дней 365");
        }
    }
}
```
