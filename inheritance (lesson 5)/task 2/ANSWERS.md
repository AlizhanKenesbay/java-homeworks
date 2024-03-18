# Ответы на домашние задания по разделу «Java» - урок 5 задача 2

## [Ссылка На Проект](https://github.com/AlizhanKenesbay/car-for-sale-program)

#### Enum Класс VehicleTypeEnum:
```java
public enum VehicleTypeEnum {
    TRUCK,CAR,PASSENGER,SEDAN,WAGON,PICKUP,BUS,PETROL,DIESEL,HYBRID,ELECTRIC
}
```
<br>

#### Класс VehicleType:
```java
public class VehicleType {
    protected String attribute;

    public VehicleType(String attribute) {
        this.attribute = attribute;
    }

    public String getAttributeOfType() {
        return attribute;
    }
    public String getTypeName() {
        return "Some vehicle type name";
    }
}
```
<br>

#### Класс VehicleTypeByPurpose наследуемый от VehicleType:
```java
public class VehicleTypeByPurpose extends VehicleType {
    public VehicleTypeByPurpose() {
        super("Vehicle type by purpose");
    }

    @Override
    public boolean equals(Object object) {
        if (object == null || getClass() != object.getClass()) return false;

        VehicleTypeByPurpose that = (VehicleTypeByPurpose) object;
        return attribute != null ? attribute.equals(that.attribute) : false;
    }
}
```

##### Класс TruckType наследуемый от VehicleTypeByPurpose:
```java
public class TruckType extends VehicleTypeByPurpose {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.TRUCK.name();
    }
}
```

##### Класс CarType наследуемый от VehicleTypeByPurpose:
```java
public class CarType extends VehicleTypeByPurpose {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.CAR.name();
    }
}
```

##### Класс PassengerType наследуемый от VehicleTypeByPurpose:
```java
public class PassengerType extends VehicleTypeByPurpose {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.PASSENGER.name();
    }
}
```
<br>

#### Класс VehicleTypeByBodyTypes наследуемый от VehicleType:
```java
public class VehicleTypeByBodyTypes extends VehicleType {
    public VehicleTypeByBodyTypes() {
        super("Vehicle type by body types");
    }

    @Override
    public boolean equals(Object object) {
        if (object == null || getClass() != object.getClass()) return false;

        VehicleTypeByBodyTypes that = (VehicleTypeByBodyTypes) object;
        return attribute != null ? attribute.equals(that.attribute) : false;
    }
}
```

##### Класс SedanType наследуемый от VehicleTypeByBodyTypes:
```java
public class SedanType extends VehicleTypeByBodyTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.SEDAN.name();
    }
}
```

##### Класс WagonType наследуемый от VehicleTypeByBodyTypes:
```java
public class WagonType extends VehicleTypeByBodyTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.WAGON.name();
    }
}
```

##### Класс PickupType наследуемый от VehicleTypeByBodyTypes:
```java
public class PickupType extends VehicleTypeByBodyTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.PICKUP.name();
    }
}
```

##### Класс BusType наследуемый от VehicleTypeByBodyTypes:
```java
public class BusType extends VehicleTypeByBodyTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.BUS.name();
    }
}
```
<br>

#### Класс VehicleTypeByFuelTypes наследуемый от VehicleType:
```java
public class VehicleTypeByFuelTypes extends VehicleType {
    public VehicleTypeByFuelTypes() {
        super("Vehicle type by fuel types");
    }

    @Override
    public boolean equals(Object object) {
        if (object == null || getClass() != object.getClass()) return false;

        VehicleTypeByFuelTypes that = (VehicleTypeByFuelTypes) object;
        return attribute != null ? attribute.equals(that.attribute) : false;
    }
}
```

##### Класс PetrolType наследуемый от VehicleTypeByFuelTypes:
```java
public class PetrolType extends VehicleTypeByFuelTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.PETROL.name();
    }
}
```

##### Класс DieselType наследуемый от VehicleTypeByFuelTypes:
```java
public class DieselType extends VehicleTypeByFuelTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.DIESEL.name();
    }
}
```

##### Класс HybridType наследуемый от VehicleTypeByFuelTypes:
```java
public class HybridType extends VehicleTypeByFuelTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.HYBRID.name();
    }
}
```

##### Класс ElectricType наследуемый от VehicleTypeByFuelTypes:
```java
public class ElectricType extends VehicleTypeByFuelTypes {

    @Override
    public String getTypeName() {
        return VehicleTypeEnum.ELECTRIC.name();
    }
}
```
<br>

#### Класс VehicleAd:
```java
public class VehicleAd {
    private String model;
    private String id;
    private VehicleTypeByPurpose vehicleTypeByPurpose;
    private VehicleTypeByBodyTypes vehicleTypeByBodyTypes;
    private VehicleTypeByFuelTypes vehicleTypeByFuelTypes;

    public VehicleAd(String model, String id, VehicleTypeByPurpose vehicleTypeByPurpose,
                     VehicleTypeByBodyTypes vehicleTypeByBodyTypes, VehicleTypeByFuelTypes vehicleTypeByFuelTypes) {
        this.model = model;
        this.id = id;
        this.vehicleTypeByPurpose = vehicleTypeByPurpose;
        this.vehicleTypeByBodyTypes = vehicleTypeByBodyTypes;
        this.vehicleTypeByFuelTypes = vehicleTypeByFuelTypes;
    }

    //for creating new Car
    public VehicleAd(String model) {
        this.model = model;
    }

    public VehicleTypeByPurpose getVehicleTypeByPurpose() {
        return vehicleTypeByPurpose;
    }

    public VehicleTypeByBodyTypes getVehicleTypeByBodyTypes() {
        return vehicleTypeByBodyTypes;
    }

    public VehicleTypeByFuelTypes getVehicleTypeByFuelTypes() {
        return vehicleTypeByFuelTypes;
    }

    public String getModel() {
        return model;
    }

    public String getId() {
        return id;
    }

    public String toString(){
        return this.model;
    }
}
```
<br>

#### Класс AdsService:
```java
public class AdsService {
    private VehicleAd[] adList;

    public void setAdList(VehicleAd[] adList) {
        this.adList = adList;
    }

    public void filterByVehicleTypeByPurpose(VehicleTypeByPurpose vehicleType) {
        for (VehicleAd ad : adList) {
            if (ad.getVehicleTypeByPurpose().equals(vehicleType)) {
                System.out.println("Объявление № " + ad.getId() + " подходит под данный фильтр с атрибутом: тип авто - "
                        + vehicleType.getTypeName() + ", атрибут фильтра " + vehicleType.getAttributeOfType());
            } else {
                System.out.println("Объявление № " + ad.getId() + " не прошло фильтр: тип авто - " + vehicleType.getTypeName() + ", критерий - " +
                        vehicleType.getAttributeOfType() + ", так как имеет тип авто " +
                        ad.getVehicleTypeByPurpose().getTypeName());
            }
        }
    }

    public void filterByVehicleTypeByBody(VehicleTypeByBodyTypes vehicleType) {
        for(VehicleAd ad : adList) {
            if(ad.getVehicleTypeByBodyTypes().equals(vehicleType)){
                System.out.println("Объявление № " + ad.getId() + " подходит под данный с атрибутом: тип авто - "
                        + vehicleType.getTypeName() + ", атрибут фильтра " + vehicleType.getAttributeOfType());
            } else {
                System.out.println("Объявление № " + ad.getId() + " не прошло фильтр: тип авто - " + vehicleType.getTypeName() +  ", критерий - " +
                        vehicleType.getAttributeOfType() + ", так как имеет тип авто " +
                        ad.getVehicleTypeByBodyTypes().getTypeName());
            }
        }
    }

    public void filterByVehicleTypeByFuel(VehicleTypeByFuelTypes vehicleType) {
        for(VehicleAd ad : adList) {
            if(ad.getVehicleTypeByFuelTypes().equals(vehicleType)){
                System.out.println("Объявление № " + ad.getId() + " подходит под данный с атрибутом: тип авто - "
                        + vehicleType.getTypeName() + ", атрибут фильтра " + vehicleType.getAttributeOfType());
            } else {
                System.out.println("Объявление № " + ad.getId() + " не прошло фильтр: тип авто - " + vehicleType.getTypeName() +  ", критерий - " +
                        vehicleType.getAttributeOfType() + ", так как имеет тип авто " +
                        ad.getVehicleTypeByFuelTypes().getTypeName());
            }
        }
    }
}
```
<br>

#### Класс Main:
```java
public class Main {
    public static void main(String[] args) {
        AdsService adsService = new AdsService();
        VehicleAd volvoAd = new VehicleAd("Volvo", "23", new PassengerType(), new SedanType(), new PetrolType());
        VehicleAd kamazAd = new VehicleAd("Kamaz", "45", new TruckType(), new PickupType(), new DieselType());
        VehicleAd hyundaiAd = new VehicleAd("Hyundai", "71", new CarType(), new SedanType(), new PetrolType());

        adsService.setAdList(new VehicleAd[]{volvoAd, kamazAd, hyundaiAd});
        adsService.filterByVehicleTypeByFuel(new PetrolType());

        System.out.println();

        adsService.filterByVehicleTypeByPurpose(new TruckType());
    }
}
```
