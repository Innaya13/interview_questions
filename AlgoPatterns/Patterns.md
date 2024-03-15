# Patterns

+ [Строитель](#строитель)



## Строитель


🏗️ Паттерн проектирования "Строитель" (Builder) относится к классу порождающих паттернов. Он позволяет создавать сложные объекты пошагово, без необходимости знать все детали конструкции заранее. 

✨ Главная идея паттерна строитель заключается в разделении процесса создания объекта на отдельные шаги (строительные методы), что позволяет поэтапно конструировать сложные объекты. Каждый шаг отвечает за установку определенной части состояния объекта. 

🔨 Основные участники паттерна строитель:
1. Строитель (Builder): определяет интерфейс для создания различных частей продукта и методы для их сборки.
2. Конкретный строитель (Concrete Builder): реализует интерфейс Строителя и предоставляет конкретную реализацию для каждого шага конструирования.
3. Продукт (Product): представляет сложный объект, который должен быть построен. Продукт состоит из различных частей, собираемых строителем.
4. Директор (Director): отвечает за последовательность шагов конструирования, работает с объектом Строителя для создания продукта.

🔧 Процесс построения объекта с использованием паттерна строитель может выглядеть следующим образом:
1. Создание объекта Строителя.
2. Установка начальных параметров объекта Строителя (если необходимо).
3. Последовательное вызов строительных методов объекта Строителя для установки всех необходимых частей объекта.
4. Возврат готового продукта от объекта Строителя.

🌟 Преимущества использования паттерна строитель:
- Позволяет создавать сложные объекты путем пошагового конструирования.
- Изолирует код, отвечающий за конструирование объекта, от его представления и внутреннего устройства.
- Упрощает процесс добавления новых типов продуктов, расширения и изменения конструирования.

❗️ Замечание:
Паттерн строитель иногда может быть излишне сложным для простых объектов или тех случаев, когда создание объекта состоит всего из нескольких шагов. В таких ситуациях его использование может показаться избыточным.

Конечно! Вот пример реализации паттерна "Строитель" (Builder) на языке Java:

```java
// Продукт
class House {
    private String foundation;
    private String walls;
    private String roof;
    
    // геттеры и сеттеры для полей
    
    @Override
    public String toString() {
        return "House with " + foundation + " foundation, " + walls + " walls, and " + roof + " roof.";
    }
}

// Строитель
interface HouseBuilder {
    void buildFoundation();
    void buildWalls();
    void buildRoof();
    House getHouse();
}

// Конкретный строитель
class ConcreteHouseBuilder implements HouseBuilder {
    private House house;
    
    public ConcreteHouseBuilder() {
        this.house = new House();
    }
    
    @Override
    public void buildFoundation() {
        house.setFoundation("concrete");
    }
    
    @Override
    public void buildWalls() {
        house.setWalls("bricks");
    }
    
    @Override
    public void buildRoof() {
        house.setRoof("tiles");
    }
    
    @Override
    public House getHouse() {
        return house;
    }
}

// Директор
class HouseDirector {
    public House constructHouse(HouseBuilder builder) {
        builder.buildFoundation();
        builder.buildWalls();
        builder.buildRoof();
        return builder.getHouse();
    }
}

// Пример использования
public class Main {
    public static void main(String[] args) {
        HouseBuilder builder = new ConcreteHouseBuilder();
        HouseDirector director = new HouseDirector();
        
        House house = director.constructHouse(builder);
        
        System.out.println(house);
    }
}
```

В этом примере мы создаем объект `House` с помощью паттерна строитель. Класс `House` представляет продукт, который мы хотим построить. Интерфейс `HouseBuilder` определяет методы для пошагового конструирования дома, а класс `ConcreteHouseBuilder` реализует эти методы для создания конкретной реализации дома.

Класс `HouseDirector` отвечает за последовательность шагов конструирования и работает с объектом `HouseBuilder`, чтобы создать и получить готовый дом.

В методе `main` мы создаем конкретного строителя `ConcreteHouseBuilder`, передаем его в директор и вызываем метод `constructHouse`, чтобы получить готовый объект `House`. Затем мы выводим информацию о доме на консоль.

🏠 В результате выполнения этого примера на консоли будет выведено: "House with concrete foundation, bricks walls, and tiles roof."

[К оглавлению](#patterns)