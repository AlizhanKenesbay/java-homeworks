# Ответы на домашние задания по разделу «Java» - урок 6 задача 2

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/accountant-task)

#### Класс Bill:
```java
import java.math.BigDecimal;

public class Bill {
    private BigDecimal amount;
    private TaxType taxType;
    private TaxService taxService;

    public Bill(BigDecimal amount, TaxType taxType, TaxService taxService) {
        this.amount = amount;
        this.taxType = taxType;
        this.taxService = taxService;
    }

    public void payTaxes() {
        BigDecimal taxAmount = taxType.calculateTaxFor(amount);

        taxService.payOut(taxAmount);
    }
}
```
<br>

#### Класс TaxService:
```java
import java.math.BigDecimal;

class TaxService {
    public void payOut(BigDecimal taxAmount) {
        System.out.format("Уплачен налог в размере %.2f%n", taxAmount);
    }
}
```
<br>

#### Класс TaxType:
```java
import java.math.BigDecimal;

class TaxType {
    public BigDecimal calculateTaxFor(BigDecimal amount) {
        return new BigDecimal("0.0");
    }
}
```

#### Класс IncomeTaxType наследуемый от TaxType:
```java
import java.math.BigDecimal;

public class IncomeTaxType extends TaxType {
    @Override
    public BigDecimal calculateTaxFor(BigDecimal amount) {
        return amount.multiply(new BigDecimal("0.13"));
    }
}
```

#### Класс VATaxType наследуемый от TaxType:
```java
import java.math.BigDecimal;

public class VATaxType extends TaxType {
    @Override
    public BigDecimal calculateTaxFor(BigDecimal amount) {
        return amount.multiply(new BigDecimal("0.18"));
    }
}
```

#### Класс ProgressiveTaxType наследуемый от TaxType:
```java
import java.math.BigDecimal;

public class ProgressiveTaxType extends TaxType {
    @Override
    public BigDecimal calculateTaxFor(BigDecimal amount) {
         BigDecimal comparableValue = new BigDecimal("100000");
        if (amount.compareTo(comparableValue) < 0) { // first value is greater
            return amount.multiply(new BigDecimal("0.10"));
        } else { // second value is greater or equal
            return amount.multiply(new BigDecimal("0.15"));
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
        TaxService taxService = new TaxService();
        Bill[] payments = new Bill[] {
                new Bill(new BigDecimal(43000), new IncomeTaxType(), taxService),
                new Bill(new BigDecimal(5000), new VATaxType(), taxService),
                new Bill(new BigDecimal(100500), new ProgressiveTaxType(), taxService),
        };

        for (Bill bill : payments) {
            bill.payTaxes();
        }
    }
}
```
