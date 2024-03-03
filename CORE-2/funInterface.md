# Функциональные интерфейсы

+ [Что такое функциональный интерфейс?](#что-такое-функциональный-интерфейс-примеры)
+ [Для чего нужна аннотация @FunctionalInterface?](#для-чего-нужна-аннотация-functionalinterface)
+ [Какие встроенные функциональные интерфейсы вы знаете?](#какие-встроенные-функциональные-интерфейсы-вы-знаете)
+ [Все способы реализации функционального интерфейса?](#все-способы-реализации-функционального-интерфейса)
+ [Что такое ссылка на метод?](#что-такое-ссылка-на-метод)
+ [Что такое лямбда-выражение? Чем его можно заменить? Как можно и как нельзя?](#что-такое-лямбда-выражение-чем-его-можно-заменить)


## Что такое функциональный интерфейс? Примеры

<img width="601" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/387592a4-1ab2-4388-a0f8-0c40649a6a82">

Функциональный интерфейс - это интерфейс, который определяет только один абстрактный метод.

Основное назначение – использование в лямбда выражениях и method reference.

Интерфейс может включать сколько угодно default методов и при этом оставаться функциональным,потому что default методы - не абстрактные.

Интерфейс называется функциональным, если в нём ровно один абстрактный метод (то есть описание метода без тела).

Ограничений по количеству методов и полей в функциональном интерфейсе нет (кроме абстрактного метода). Многие функциональные интерфейсы, предоставляемые Java8, находятся в пакете java.util.function

<img width="1100" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/0c388b86-d06e-4f26-82ac-5df4291e1a22">

Зачем нужен?
Когда в Java нужно передать в метод кусочек программной логики, то метод объявляется, как принимающий экземпляр какого-то класса или интерфейса.


В Java функциональный интерфейс - это интерфейс, который содержит только один абстрактный метод. Такой интерфейс используется для работы с лямбда-выражениями и методами ссылок, что позволяет удобно передавать поведение в виде объекта.

Для создания функционального интерфейса в Java 8 и выше, вы можете использовать аннотацию `@FunctionalInterface`. Если интерфейс содержит более одного абстрактного метода или не содержит абстрактных методов вовсе, компилятор выдаст ошибку.

Вот пример простого функционального интерфейса:

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void doSomething(); // Абстрактный метод, который должен быть реализован
}
```

Теперь давайте рассмотрим некоторые стандартные функциональные интерфейсы, предоставляемые Java в пакете `java.util.function`:

1. `Consumer<T>`: Принимает аргумент типа T, выполняет операции, но ничего не возвращает.

```java
import java.util.function.Consumer;

public class ExampleConsumer {
    public static void main(String[] args) {
        Consumer<String> printUpperCase = str -> System.out.println(str.toUpperCase());
        printUpperCase.accept("hello"); // Выведет "HELLO"
    }
}
```

2. `Supplier<T>`: Не принимает аргументов, но возвращает значение типа T.

```java
import java.util.function.Supplier;

public class ExampleSupplier {
    public static void main(String[] args) {
        Supplier<Double> randomNumber = () -> Math.random();
        System.out.println(randomNumber.get()); // Выведет случайное число
    }
}
```

3. `Function<T, R>`: Принимает аргумент типа T, выполняет операции и возвращает результат типа R.

```java
import java.util.function.Function;

public class ExampleFunction {
    public static void main(String[] args) {
        Function<Integer, String> intToString = num -> "Number: " + num;
        System.out.println(intToString.apply(42)); // Выведет "Number: 42"
    }
}
```

4. `Predicate<T>`: Принимает аргумент типа T и возвращает `true` или `false` в зависимости от условия.

```java
import java.util.function.Predicate;

public class ExamplePredicate {
    public static void main(String[] args) {
        Predicate<Integer> isEven = num -> num % 2 == 0;
        System.out.println(isEven.test(5)); // Выведет "false"
    }
}
```

Это лишь несколько примеров функциональных интерфейсов в Java. Java API предоставляет и другие функциональные интерфейсы, которые могут быть полезны в различных сценариях программирования.

[к оглавлению](#функциональные-интерфейсы)

## Для чего нужна аннотация @FunctionalInterface?

Чтобы точно определить интерфейс как функциональный, добавлена аннотация @FunctionalInterface,работающая по принципу @Override. Она обозначит замысел и не даст определить второй абстрактный метод в интерфейсе.

Если же в интерфейсе с данной аннотацией более одного не реализованного (абстрактного) метода, компилятор не пропустит данный интерфейс, так как будет воспринимать его как ошибочный код.

Интерфейсы и без данной аннотации могут считаться функциональными и будут работать, а @FunctionalInterface является не более чем дополнительной страховкой.

[к оглавлению](#функциональные-интерфейсы)

## Какие встроенные функциональные интерфейсы вы знаете?

https://javarush.com/groups/posts/3981-kofe-breyk-182-funkcionaljhnihe-interfeysih-v-java

Встроенные функциональные интерфейсы:

+ Predicate<T> Проверяет соблюдение некоторого условия. Если оно соблюдается, то возвращается значение true. В качестве параметра лямбда-выражение принимает объект типа T
+ Consumer<T> выполняет некоторое действие над объектом типа T, при этом ничего не возвращая
+ Function<T,R> представляет функцию перехода от объекта типа T к объекту типа R
+ Supplier<T> не принимает никаких аргументов, но должен возвращать объект типа T
+ UnaryOperator<T> принимает в качестве параметра объект типа T, выполняет над ними операции и возвращает результат операций в виде объекта типа T
+ BinaryOperator<T> принимает в качестве параметра два объекта типа T, выполняет над ними бинарную операцию и возвращает ее результат также в виде объекта типа T
+ плюс Интерфейс `Comparator` определяет методы для сравнения двух объектов. Он широко используется для сортировки объектов в коллекциях или других структурах данных. В частности, метод `compare(T o1, T o2)` в этом интерфейсе используется для сравнения двух объектов типа `T` - он уже как реализации одного из интерфейсов выше

**Predicate<T> принимает значение, отдаёт булевское true или false**

<img width="414" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/426d5140-5b42-4949-be86-acdd6082ed67">

Функциональный интерфейс Predicate<T> проверяет соблюдение некоторого условия. Если оно соблюдается, то возвращается значение true.
В качестве параметра лямбда-выражение принимает объект типа T:

<img width="668" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/c2416670-078b-4fee-b82a-4b13565534e8">

**Операторы – это частный случай функции, когда на входе и на выходе значения одного и того же типа.**

**UnaryOperator<T> унарный оператор**

<img width="435" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/1fc06da0-b61b-49d3-9406-8ed134fea322">

UnaryOperator<T> принимает в качестве параметра ОДИН объект типа T, выполняет над ними операции и возвращает результат операций в виде объекта типа T.

**BinaryOperator<T> бинарный оператор**

BinaryOperator<T> принимает в качестве параметра ДВА объекта типа T, выполняет над ними бинарную  операцию и возвращает ее результат также в виде объекта типа T.

**Function<T,R> функции принимают/возвращают**

T - входной параметр (принимает); R - return type (возвращает)

<img width="509" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/b4a0580b-4623-4bd2-a64c-bd49300db7b9">

Функциональный интерфейс Function<T,R> представляет функцию перехода от объекта типа T к объекту типа  R.

<img width="1151" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/0406f7b6-bd9c-4e25-8281-e50171923272">

**Consumer<T> потребитель только принимает**

<img width="432" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/94d1a949-f75e-4037-bba0-30c03881cd99">

Consumer<T> выполняет некоторое действие над объектом типа T, при этом ничего не возвращая:

<img width="642" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/b1a76c4a-5144-43ba-b140-3937af2466b3">

**Supplier<T> поставщик только поставляет**

<img width="505" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/86b36d8a-d3f2-48fd-b30c-b4ec2411c342">

Supplier<T> не принимает никаких аргументов, но должен возвращать объект типа T:

<img width="642" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/9e6c04bb-6400-472a-8c57-d26a673444f8">

[к оглавлению](#функциональные-интерфейсы)

## Все способы реализации функционального интерфейса?

В Java 8 функциональные интерфейсы могут быть представлены с использованием лямбда-выражений, ссылок на методы и ссылок на конструкторы.

<img width="1102" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/5b9e4ced-6de2-4f60-aa4e-2fa478c36a23">

[к оглавлению](#функциональные-интерфейсы)

## Что такое ссылка на метод?

Ссылки на методы (Method References) – это компактные лямбда выражения для методов, у которых уже есть имя.

Ссылки на методы бывают четырех видов:

Ссылка на статический метод - ContainingClass::staticMethodName
```java
Function<String, Boolean> function = e -> Boolean.valueOf(e);

System.out.println(function.apply(\"TRUE\"));

Function<String, Boolean> function = Boolean::valueOf;

System.out.println(function.apply(\"TRUE\"));
```
Ссылка на нестатический метод конкретного объекта - containingObject::instanceMethodName
```java
Consumer<String> consumer = e -> System.out.println(e);

consumer.accept(\"OCPJP 8\");

Consumer<String> consumer = System.out::println;

consumer.accept(\"OCPJP 8\");
```
Ссылка на нестатический метод любого объекта конкретного типа - ContainingType::methodName
```java
Function<String, String> function = s -> s.toLowerCase();

System.out.println(function.apply(\"OCPJP 8\"));

Function<String, String> function = String::toLowerCase;

System.out.println(function.apply(\"OCPJP 8\"));
```
Ссылка на конструктор ClassName::new
```java
Function<String, Integer> function = (d) -> new Integer(d);

System.out.println(function.apply(\"4\"));

Function<String, Integer> function = Integer::new;

System.out.println(function.apply(\"4\"));
```
Если лямбда выражения вызывают только один существующий метод, лучше ссылать на этот метод по его имени. Ссылки на методы (Method References) – это компактные лямбда выражения для методов, у которых уже есть имя.

<img width="761" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/49e09e3d-530f-4349-bf42-62b209621012">

[к оглавлению](#функциональные-интерфейсы)

## Что такое лямбда-выражение? Чем его можно заменить?

Лямбда-выражения или анонимные функции — это блоки кода с параметрами, которые можно вызвать из другого места программы. Они называются анонимными, потому что в отличие от функций, у них нет имён.

Представляет набор инструкций, которые можно выделить в отдельную переменную и затем многократно вызвать в различных местах программы. Образует реализацию метода, определенного в функциональном интерфейсе. При этом важно, что функциональный интерфейс должен содержать только один единственный метод без реализации.

список параметров выражения -> тело лямбда-выражения (действия)

Параметры лямбда-выражения должны соответствовать по типу параметрам метода из функционального интерфейса.

В лямбда-выражении использование обобщений не допускается. В этом случае нам надо типизировать объект интерфейса определенным типом, который потом будет применяться в лямбда-выражении.
```java
public class LambdaApp {

    public static void main(String[] args) {

        Operationable<Integer> operation1 = (x, y)-> x + y;

        Operationable<String> operation2 = (x, y) -> x + y;

        System.out.println(operation1.calculate(20, 10)); //30

        System.out.println(operation2.calculate(\"20\", \"10\")); //2010

    } 

}

interface Operationable<T>{

    T calculate(T x, T y);

}
```
Одним из ключевых моментов в использовании лямбд является отложенное выполнение (deferred execution). То есть мы определяем в одном месте программы лямбда-выражение и затем можем его вызывать при необходимости неопределенное количество раз в различных частях программы. Отложенное выполнение может потребоваться, к примеру, в следующих случаях:

+ Выполнение кода отдельном потоке
+ Выполнение одного и того же кода несколько раз
+ Выполнение кода в результате какого-то события
+ Выполнение кода только в том случае, когда он действительно необходим и если он необходим

Лямбда-выражение или просто лямбда в Java — упрощённая запись анонимного класса, реализующего ТОЛЬКО функциональный интерфейс.

<img width="314" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/0cd6fbdd-f4f8-4660-bef2-f0413edf8672">

<img width="1137" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/ae11969a-d6a2-463c-8bf0-795c80ad6091">

<img width="565" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/5f3418ee-ab60-480e-9098-1a515367cfed">

https://www.youtube.com/watch?v=DgshYDTpS9I

<img width="476" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/74f742f7-735d-44b8-ad48-f47c4bedd40a">

<img width="532" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/64a8ff04-9328-48a1-99ff-c9c45ee25fb9">

<img width="558" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/9bc4d17e-d1b9-45e4-a1d2-4ba21a1b8da4">

<img width="1129" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/961bd779-e85d-4e8e-ba76-146acd8e72e1">

**Как можно и как нельзя? Иногда на собеседованиях просят найти ошибку в коде.**

<img width="1000" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/efc0c94b-b581-4675-96fb-0c64eae6d290">

<img width="1117" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/199449ac-f4e7-457c-b827-f9008376a003">

<img width="959" alt="image" src="https://github.com/Oknel-Vap/Interview_questions/assets/116596752/147dcfae-4b24-4b20-a3b2-be6a216d4361">

Что можно сказать про замену лямбда-выражений:

1. **Анонимные классы**: Перед введением лямбда-выражений в Java 8, анонимные классы использовались для создания анонимных функций. Однако анонимные классы требовали больше кода и были менее читаемыми, чем лямбда-выражения.

2. **Обычные методы**: Если функциональный интерфейс уже имеет соответствующий метод в каком-либо классе, вы можете использовать ссылку на метод вместо лямбда-выражения. Например, если у вас есть функциональный интерфейс `Predicate`, вы можете использовать ссылку на метод `String::isEmpty` вместо лямбда-выражения `(str) -> str.isEmpty()`.

Что нельзя:

1. **Сложные логические операции**: Лямбда-выражения следует использовать для простых операций. Если вам нужно выполнить сложные логические операции, лучше использовать обычные методы для улучшения читаемости кода.

2. **Несовместимость с нефункциональными интерфейсами**: Лямбда-выражения могут использоваться только с функциональными интерфейсами - интерфейсами с одним абстрактным методом. Нефункциональные интерфейсы (интерфейсы с несколькими абстрактными методами) не могут быть заменены лямбда-выражениями.

3. **Создание новых классов и объектов**: Лямбда-выражения не заменяют полностью классы и объекты. Они предоставляют более компактный способ определения функций, но это не заменяет создание новых классов при необходимости.

[к оглавлению](#функциональные-интерфейсы)