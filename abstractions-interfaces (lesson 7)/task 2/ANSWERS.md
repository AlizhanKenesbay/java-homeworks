# Ответы на домашние задания по разделу «Java» - урок 7 задача 2

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/bank-accounts-project)

#### Класс Account:
```java
import java.math.BigDecimal;
import java.math.RoundingMode;

public abstract class Account {
    BigDecimal balance = new BigDecimal(0);

    public abstract void pay(BigDecimal amount);

    public abstract void transfer(Account account, BigDecimal amount);

    public abstract void addMoney(BigDecimal amount);

    public BigDecimal getBalance() {
        return balance.setScale(2, RoundingMode.CEILING);
    }
}
```

#### Класс SavingsAccount наследуемый от Account:
```java
import java.math.BigDecimal;

public class SavingsAccount extends Account {

    @Override
    public void pay(BigDecimal amount) {
        System.out.println("Вы не можете оплатить со сберегательного счета");
    }

    @Override
    public void transfer(Account account, BigDecimal amount) {
        if (balance.compareTo(amount) >= 0) { // if (balance >= amount)
            balance = balance.subtract(amount);
            account.addMoney(amount);
            if (account instanceof CreditAccount) {
                System.out.println("Перевод на кредитный счет в размере " + amount + " был выполнен");
            } else if (account instanceof CheckingAccount) {
                System.out.println("Перевод на расчетный счет в размере " + amount + " был выполнен");
            } else {
                System.out.println("Ошибка, счет не найден");
            }
        } else {
            System.out.println("Недостаточно денег для перевода");
        }
    }

    @Override
    public void addMoney(BigDecimal amount) {
        if (amount.compareTo(BigDecimal.ZERO) >= 0) { // if (amount >= 0)
            balance = balance.add(amount);
            System.out.println("Баланс сберегательного счета пополнен на: " + amount);
        } else {
            System.out.println("Ошибка, введена отрицательная сумма");
        }
    }
}
```

#### Класс CreditAccount наследуемый от Account:
```java
import java.math.BigDecimal;

public class CreditAccount extends Account {
    @Override
    public void pay(BigDecimal amount) {
        if (balance.compareTo(BigDecimal.ZERO) <= 0) { // if (balance <= 0)
            balance = balance.subtract(amount);
            System.out.println("Оплата прошла успешно");
        } else {
            System.out.println("Ошибка, ваш счет имеет положительный баланс");
        }
    }

    @Override
    public void transfer(Account account, BigDecimal amount) {
        if (balance.compareTo(BigDecimal.ZERO) <= 0) { // if (balance <= 0)
            balance = balance.subtract(amount);
            account.addMoney(amount);
            if (account instanceof SavingsAccount) {
                System.out.println("Перевод на сберегательный счет в размере " + amount + " был выполнен");
            } else if (account instanceof CheckingAccount) {
                System.out.println("Перевод на расчетный счет в размере " + amount + " был выполнен");
            } else {
                System.out.println("Ошибка, счет не найден");
            }
        } else {
            System.out.println("Недостаточно денег для перевода");
        }
    }

    @Override
    public void addMoney(BigDecimal amount) {
        BigDecimal potentialBalance = balance.add(amount);

        if (potentialBalance.compareTo(BigDecimal.ZERO) >= 0) { // if (potentialBalance >= 0)
            balance = BigDecimal.ZERO;
            System.out.println("Баланс кредитного счета пополнен на: " + amount);
        } else {
            System.out.println("Ошибка, введена отрицательная сумма");
        }
    }
}
```

#### Класс CheckingAccount наследуемый от Account:
```java
import java.math.BigDecimal;

public class CheckingAccount extends Account {
    @Override
    public void pay(BigDecimal amount) {
        if (balance.compareTo(amount) >= 0) { // if (balance >= amount)
            balance = balance.subtract(amount);
            System.out.println("Оплата прошла успешно");
        } else {
            System.out.println("Ошибка, ваш счет имеет положительный баланс");
        }
    }

    @Override
    public void transfer(Account account, BigDecimal amount) {
        if (balance.compareTo(amount) >= 0) { // if (balance >= amount)
            balance = balance.subtract(amount);
            account.addMoney(amount);
            if (account instanceof SavingsAccount) {
                System.out.println("Перевод на сберегательный счет в размере " + amount + " был выполнен");
            } else if (account instanceof CreditAccount) {
                System.out.println("Перевод на кредитный счет в размере " + amount + " был выполнен");
            } else {
                System.out.println("Ошибка, счет не найден");
            }
        } else {
            System.out.println("Недостаточно денег для перевода");
        }
    }

    @Override
    public void addMoney(BigDecimal amount) {
        if (amount.compareTo(BigDecimal.ZERO) >= 0) { // if (amount >= 0)
            balance = balance.add(amount);
            System.out.println("Баланс сберегательного счета пополнен на: " + amount);
        } else {
            System.out.println("Ошибка, введена отрицательная сумма");
        }
    }
}
```
<br>

#### Класс Main:
```java
import java.math.BigDecimal;

public class Main {
    public static void main(String[] args) {
        SavingsAccount savingsAccount = new SavingsAccount();
        CreditAccount creditAccount = new CreditAccount();
        CheckingAccount checkingAccount = new CheckingAccount();

        savingsAccount.addMoney(BigDecimal.valueOf(1000.438));
        creditAccount.addMoney(BigDecimal.valueOf(1000.756));
        checkingAccount.addMoney(BigDecimal.valueOf(-5000.1));
        System.out.println();

        System.out.println("Баланс на сберегательном счету: " + savingsAccount.getBalance());
        System.out.println("Баланс на кредитном счету: " + creditAccount.getBalance());
        System.out.println("Баланс на расчетном счету: " + checkingAccount.getBalance());
        System.out.println();

        savingsAccount.pay(BigDecimal.valueOf(1000));
        savingsAccount.transfer(creditAccount, BigDecimal.valueOf(1));
        savingsAccount.addMoney(BigDecimal.valueOf(5000.52));
        System.out.println();

        creditAccount.addMoney(BigDecimal.valueOf(1000));
        System.out.println("Баланс на кредитном счету: " + creditAccount.getBalance());
        creditAccount.transfer(savingsAccount, BigDecimal.valueOf(1000));
        System.out.println("Баланс на кредитном счету: " + creditAccount.getBalance());
    }
}
```