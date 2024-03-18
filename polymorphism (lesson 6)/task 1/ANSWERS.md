# Ответы на домашние задания по разделу «Java» - урок 6 задача 1

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/shooter-game)

#### Класс Player:
```java
import weapon.*;

public class Player {
    private Weapon[] weaponSlots;

    public Player() {
        weaponSlots = new Weapon[] {
            new Pistol(),
            new AssaultRifle(),
            new RPG(),
            new Slingshot(),
            new WaterGun()
        };
    }

    public void printWeaponSlots() {
        int i = 0;
        for (Weapon weapon : weaponSlots) {
            System.out.println(i + ". " + weapon.getName());
            i++;
        }
    }

    public int getSlotsCount() {
        return weaponSlots.length;
    }

    public void shotWithWeapon(int slot) {
        if (slot > weaponSlots.length - 1) {
            System.out.println("Неправильное значение слота");
        }
        Weapon weapon = weaponSlots[slot];
        weapon.shot();
    }
}
```
<br>

#### Класс Weapon:
```java
package weapon;

public class Weapon {
    private String name;
    public void shot() {

    }

    public String getName() {
        return name;
    }
}
```

#### Класс Pistol наследуемый от Weapon:
```java
package weapon;

public class Pistol extends Weapon {
    private String name = "Пистолет";
    @Override
    public void shot() {
        System.out.println("бах-бах");
    }

    public String getName() {
        return name;
    }
}
```

#### Класс AssaultRifle наследуемый от Weapon:
```java
package weapon;

public class AssaultRifle extends Weapon {
     String name = "Автомат";
    @Override
    public void shot() {
        System.out.println("тра-та-та-та-та");
    }

    public String getName() {
        return name;
    }
}
```

#### Класс RPG наследуемый от Weapon:
```java
package weapon;

public class RPG extends Weapon {
    private String name = "РПГ";
    @Override
    public void shot() {
        System.out.println("БУУМ");
    }

    public String getName() {
        return name;
    }
}
```

#### Класс Slingshot наследуемый от Weapon:
```java
package weapon;

public class Slingshot extends Weapon {
    private String name = "Рогатка";
    @Override
    public void shot() {
        System.out.println("швырь-швырь");
    }

    public String getName() {
        return name;
    }
}
```

#### Класс WaterGun наследуемый от Weapon:
```java
package weapon;

public class WaterGun extends Weapon {
    private String name = "Водяной пистолет";
    @Override
    public void shot() {
        System.out.println("шшш-пшик");
    }

    public String getName() {
        return name;
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
        Player player = new Player();
        System.out.printf("У игрока %d слотов с оружием,"
                + " введите номер, чтобы выстрелить из выбранного оружия,"
                + " -1 чтобы выйти%n",
                player.getSlotsCount()
        );

        int slot;

        while (true) {
            System.out.println("Введите номер слота с оружем: ");
            player.printWeaponSlots();
            slot = scanner.nextInt();
            if (slot == -1) {
                break;
            } else {
                player.shotWithWeapon(slot);
            }
        }
    }
}
```
