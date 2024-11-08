[Вопросы для собеседования](https://github.com/Oknel-Vap/Interview_questions/blob/main/QUESTIONS.md#interview_questions)

# Java

+ [Какая основная идея языка?](#Какая-основная-идея-языка)
+ [За счет чего обеспечивается кроссплатформенность?](#За-счет-чего-обеспечивается-кроссплатформенность)
+ [Какие преимущества у java?](#Какие-преимущества-у-java)
+ [Какие недостатки у Java?](#Какие-недостатки-у-Java)
+ [Что такое JDK? Что в него входит?](#Что-такое-JDK)
+ [Что такое JRE? что в него входит?](#Что-такое-JRE)
+ [Что такое JVM?](#Что-такое-JVM)
+ [Что такое byte code?](#Что-такое-byte-code)
+ [Что такое загрузчик классов (classloader)?](#что-такое-загрузчик-классов-classloader)
+ [Что такое JIT?](#Что-такое-JIT)
+ [Что такое сборщик мусора? (Garbage collector)](#Что-такое-сборщик-мусора)
+ [Что такое Heap и Stack память в Java? Чем они отличаются?](#что-такое-heap-и-stack-память-в-java-чем-они-отличаются)

## Какая основная идея языка?

Кроссплатформенность - «написано/скомпилировано однажды, запускается везде» (compile once, run anywhere).
Приложения Java обычно транслируются в специальный байт-код, поэтому они могут работать на любой компьютерной архитектуре, для которой существует реализация виртуальной Java- машины.
Байт-код Java - набор инструкций, исполняемых виртуальной машиной Java. Каждый код операции байт-кода - один байт. Используются не все 256 возможных значений кодов операций. 51 из них зарезервированы для использования в будущем. 

Основная идея была в том, что программный код исполняется не напрямую процессором, а интерпретатором байт-кода называемом java-машиной или JVM. Такой подход несет ряд особенностей и дает множество преимуществ. Кроссплатформенность. Джава-машины умеют обрабатывать универсальные инструкции байт-кода с учетом конкретных особенностей систем. Именно поэтому данный язык захватил разработку под мобильные устройства.

[к оглавлению](#java)

## За счет чего обеспечивается кроссплатформенность?

Java Virtual Machine (JVM) - виртуальная машина Java - основная часть исполняющей системы Java, так называемой Java Runtime Environment (JRE).

Виртуальная машина Java исполняет байт-код Java, предварительно созданный из исходного текста Java-программы компилятором Java (javac). JVM может также использоваться для выполнения программ, написанных на других языках программирования.

Например, исходный код на языке Ada может быть скомпилирован в байт-код Java, который затем может выполниться с помощью JVM. 

![](images/jvm.png)

[к оглавлению](#java)

## Какие преимущества у java?

+ Объектно-ориентированный: все является объектом. Дополнение может быть легко расширено.
+ Платформонезависимый
+ Простой для понимания: основные концепции ООП.
+ Безопасный: методы проверки подлинности основаны на шифровании с открытым ключом.
+ Архитектурно-нейтральный: компилятор генерирует архитектурно-нейтральные объекты формата файла, что делает скомпилированный код исполняемым на многих процессорах, с наличием системе Java Runtime.
+ Портативный: архитектурно-нейтральный и не имеющий зависимости от реализации аспектов спецификаций - все это делает Java портативным. Компилятор в Java написан на ANSI C с чистой переносимостью, который является подмножеством POSIX.
+ Прочный: прилагает усилия, чтобы устранить ошибки в различных ситуациях, делая упор в основном на время компиляции, проверку ошибок и проверку во время выполнения.
+ Язык для распределенного программирования и комфортной удаленной совместной работы.
  _Специфическая для Java методология распределенных вычислений называется Remote Method Invocation (RMI). RMI позволяет использовать все преимущества Java: безопасность, независимость от платформы и объектно-ориентированное программирование для распределенных вычислений._
+ Автоматическое управление памятью
+ Многопоточность
+ Стабильность и сообщество

### Отличительные особенности Java

* **Переносимость** - выполнение программы в разных системах (процессорах, операционных системах).
Один и тот же код работает на всех системах (точнее говоря, в JVM, реализованных для этих систем). Переносимость
_достигается с помощью байт-кода и выполнении его в JVM_.
Слоган "Написано однажды, работает везде" (Write once, run anywhere/everywhere).
* **Безопасность** - Java-программа выполняется в исполняющей среде, которая изолирует программу от ресурсов ОС.
* **Простота** - синтаксически язык относительно простой, но в то же время мощный благодаря огромной библиотеке
Java-классов.
* **Статическая типизация** - если объявили переменную как String, мы не можем переобъявить её как Integer (как например это возможно в Python). То есть мы уверены в типе переменной. 
* **Объектная ориентированность** - "всё является объектом". Одновременно, примитивные типы данных не являются
объектами для увеличения производительности.
* **Надёжность**. Т.к. Java-программы выполняются в разнотипных системах, то для обеспечения надёжности на язык
накладывается ряд ограничений, которые также облегчают работу программиста. Это:
  * строгая типизация языка - проверка типов во время компиляции (во время выполнения проверка также выполняется);
  * автоматическое управление выделением и освобождением оперативной памяти (освобождение с помощью сборщика мусора);
  * объектно-ориентированный механизм обработки исключений.
* **Многопоточность** - поддержка написания многопоточных программ. Исполняющая система Java решает сложные вопросы
синхронизации процессов.
* **Архитектурная нейтральность** - независимость языка от изменяющихся операционных систем и процессоров для
достижения долговечности и переносимости кода. Например, постоянные размеры элементарных типов данных, независимо от
разрядности системы.
* **Интерпретируемость и высокая производительность** - компиляция в байт-код, интерпретируемый виртуальной машиной JVM.
Вместе с этим, JIT-компилятор выполняет налету компиляцию частей байт-кода в машиннозависимый, увеличивая
производительность. По последним оценкам, в среднем, программа, написанная на Java, выполняется всего в 1,8 раза
медленнее программы, написанной на C. Это заслуга оптимизированного байт-кода, JIT-компилятора, JVM в целом.
* **Распределённость** - язык Java адаптирован для распределённой среды Интернета, поддерживает семейство сетевых
протоколов TCP/IP. Обращение к сетевому ресурсу по унифицированному указателю информационного ресурса (URL) мало чем
отличается от обращения к файлу. Также поддерживается удалённый вызов методов (Remote Method Invocation, RMI) -
возможность вызывать методы из программ  через сеть.
* **Динамичность** - наличие в программах значительного объёма данных динамического типа. Они используются для
проверки прав и разрешения доступа к объектам во время выполнения.

[к оглавлению](#java)

## Какие недостатки у Java?

+ Плата за коммерческое использование. В 2019-м году компания Оракл приняла решение брать плату за коммерческое пользование этим ЯП (Java Standard Edition 8). Многим компаниям пришлось оценивать эффективность использования этого языка в собственных целях и искать бесплатные альтернативы. Для простого пользования Java остается абсолютно бесплатным языком.
+ Невысокая производительность. Любой высокоуровневый язык из-за использования виртуальной машины для своей компиляции обладает более низкой производительностью. Java в том числе, но не только это влияет на ее «быстроту». Также производительность падает из-за проблем с очисткой памяти, плохой настройки кэширования, вероятности взаимной блокировки потоков и т. д.
+ Отсутствует нативный дизайн. Для создания интерфейса пользователя на компьютере для java-приложения нет ни одного java-инструмента, поэтому разработчики используют сторонние инструменты и библиотеки. Отсутствие нативного дизайна для создания графического интерфейса пользователя (GUI). Есть Swing, SWT, JavaFX, JSF …но не катят.
+ Сложность и многословность кода. При написании кода есть вынужденное использование большого количества лишнего текста. Из-за этого улетучивается «компактность» языка, но в то же время это облегчает «понимание» кода неспециалистам Java.

Java - это мощный и популярный язык программирования, но у него также есть некоторые недостатки. Вот некоторые из них:

1. Низкая производительность: Java является языком программирования, выполняющимся на виртуальной машине Java (JVM), что может привести к некоторому снижению производительности по сравнению с некоторыми низкоуровневыми языками, такими как C или C++. Однако современные версии JVM и оптимизации компилятора позволяют достичь хорошей производительности во многих случаях.

2. Потребление памяти: JVM требует дополнительной памяти для выполнения и управления приложениями на Java. Это может быть проблемой в случае ограниченных ресурсов или при разработке программ для встроенных систем с ограниченной памятью.

3. Загрузка времени выполнения: Приложения на Java требуют загрузки времени выполнения (JVM), что может занимать некоторое время и увеличивать время запуска приложения. Однако, современные JVM обычно обладают хорошей оптимизацией и могут предварительно компилировать код для ускорения запуска.

4. Ограничения в GUI: Java имеет свою собственную библиотеку для создания графического интерфейса пользователя (GUI) - Swing и JavaFX. В сравнении с некоторыми другими языками и фреймворками для GUI, Java может быть менее гибким и менее простым для создания сложных пользовательских интерфейсов.

5. Отсутствие нативной поддержки некоторых возможностей: Java не предоставляет нативной поддержки для некоторых возможностей, таких как манипуляции с памятью на низком уровне или прямой доступ к аппаратным ресурсам. В некоторых случаях может потребоваться использование библиотек на других языках, таких как C или C++, для реализации таких функций.

6. Сложность многопоточности: Хотя Java предоставляет мощные средства для работы с многопоточностью, разработка безопасных и эффективных многопоточных приложений может быть сложной задачей. Неправильное использование многопоточности может привести к состояниям гонки, дедлокам и другим проблемам.

Несмотря на эти недостатки, Java остается одним из самых популярных языков программирования благодаря своей платформенной независимости, обширной экосистеме, хорошей поддержке и простоте разработки.

[к оглавлению](#java)

## Что такое JDK?

Java Development Kit (JDK) - комплект разработчика приложений на языке Java:

+ исполнительная система Java (JRE: Java Virtual Machine (JVM) + библиотеки Java-классов).
+ компилятор Java (javac)
+ стандартные библиотеки классов Java, примеры, документация, утилиты (вспомогательная компьютерная программа в составе общего программного обеспечения для выполнения специализированных типовых задач, связанных с работой оборудования и операционной системы)

_JDK позволяет разработчикам создавать программы, которые могут выполняться и запускаться посредством JVM и JRE;_

![](images/jdk.png)

JDK (Java Development Kit) - это пакет разработки Java, который включает в себя все необходимые инструменты и компоненты для разработки, отладки и выполнения Java-приложений. JDK предоставляет компилятор Java (javac), виртуальную машину Java (JVM), набор библиотек классов Java (Java Class Library) и другие утилиты, необходимые для разработки Java-приложений.

Основные компоненты JDK включают:

1. Компилятор Java (javac): Преобразует исходный код Java в байт-код, который может быть выполнен на виртуальной машине Java (JVM). Компилятор является одним из основных инструментов в JDK и используется для создания исполняемых файлов Java.

2. Виртуальная машина Java (JVM): Исполняет байт-код Java и обеспечивает выполнение Java-приложений на различных платформах. JVM интерпретирует байт-код или использует JIT (Just-In-Time) компиляцию для повышения производительности.

3. Библиотеки классов Java (Java Class Library): Содержат предопределенные классы и методы, которые облегчают разработку Java-приложений. Библиотеки классов включают различные функциональные возможности, такие как работа с файлами, сетевое взаимодействие, работа с базами данных, графический интерфейс пользователя и многое другое.

4. Другие инструменты и утилиты: JDK также включает в себя различные инструменты и утилиты, которые помогают разработчикам в процессе разработки и отладки Java-приложений. Некоторые из них включают: javadoc (для создания документации по коду), jdb (для отладки Java-приложений), jar (для создания и работы с JAR-файлами) и многие другие.

JDK является неотъемлемой частью разработки на языке Java и необходим для создания, компиляции и выполнения Java-приложений.

[к оглавлению](#java)

## Что такое JRE? 

Java Runtime Environment (JRE среда выполнения для Java) - минимальная реализация виртуальной машины, необходимая для исполнения Java-приложений, без компилятора и других средств разработки: Java Virtual Machine + и библиотеки Java-классов.

**Как JRE работает с JVM**

Виртуальная машина Java — программное обеспечение, отвечающее за выполнение Java-программ. JRE — это программа, которая берет ваш Java-код, объединяет его с необходимыми библиотеками и запускает JVM для его выполнения. JRE содержит программное обеспечение и библиотеки, которые требуются для работы вашей программы. Например, загрузчик классов Java является частью JRE. Эта важная часть программного обеспечения загружает скомпилированный Java-код в память и соединяет с соответствующими библиотеками. В этом многоуровневом представлении JVM создается средой выполнения Java. С точки зрения пакета, JRE содержит JVM, как показано на рисунке:

![](images/jre.png)

JRE (Java Runtime Environment) и JDK (Java Development Kit) - это два различных комплекта инструментов, связанных с разработкой и выполнением Java-приложений. Вот основные отличия между JRE и JDK:

JRE:
- JRE представляет собой среду выполнения Java, которая необходима для запуска Java-приложений.
- JRE включает в себя виртуальную машину Java (JVM) и библиотеки классов Java (Java Class Library), которые необходимы для выполнения Java-приложений.
- JRE не содержит инструменты и компоненты для разработки Java-приложений, такие как компилятор Java (javac) и другие инструменты разработки.
- JRE обычно устанавливается на компьютере конечного пользователя, чтобы он мог запускать Java-приложения.

JDK:
- JDK представляет собой набор инструментов разработки Java, который включает в себя все компоненты JRE, а также дополнительные инструменты и библиотеки, необходимые для разработки Java-приложений.
- JDK включает в себя компилятор Java (javac), который используется для преобразования исходного кода Java в байт-код Java.
- JDK также содержит другие инструменты разработки, такие как отладчик (debugger), профилировщик (profiler), документацию и другие утилиты, которые помогают разработчикам создавать, отлаживать и профилировать Java-приложения.
- JDK обычно используется разработчиками для создания и компиляции Java-приложений.

В общем, JRE предоставляет среду выполнения Java для запуска Java-приложений, а JDK предоставляет инструменты и библиотеки для разработки Java-приложений. Если вам нужно только запустить Java-приложение, вам потребуется JRE. Если вы планируете разрабатывать Java-приложения, вам потребуется JDK.

[к оглавлению](#java)

## Что такое JVM?

Java Virtual Machine (JVM) - это программа, предназначенная для выполнения других программ.

Это основная часть JRE. Исполняет байт-код Java, предварительно созданный из исходного текста Java-программы компилятором Java (javac). JVM может также использоваться для выполнения программ, написанных на других языках программирования.

_Например, исходный код на языке Ada может быть скомпилирован в байт-код Java, который затем может выполниться с помощью JVM_

JVM имеет две основные функции:

+ Позволяет запускать Java-приложения на любых устройствах или операционных системах.
+ Управляет и оптимизирует память, используемую приложением.

[к оглавлению](#java)

## Что такое byte code?

Промежуточное представление кода, в которое может быть переведена компьютерная программа автоматическими средствами. Машинно-независимый код низкого уровня, генерируемый транслятором из исходного кода - набор валидных (соответствующих спецификации Java) команд.

[к оглавлению](#java)

## Что такое загрузчик классов (classloader)?

[Хорошая статья по теме](https://java-online.ru/java-classloader.xhtml)

[И на javarush](https://javarush.com/groups/posts/646-kak-proiskhodit-zagruzka-klassov-v-jvm)

Загрузчик классов в Java - это программа или механизм, который отвечает за загрузку классов в память Java-виртуальной машины (JVM). Он ищет, загружает и инициализирует классы во время выполнения программы.

Загрузчики классов в Java делятся на несколько уровней или групп:

1. Загрузчик ядра (Bootstrap Class Loader): Этот загрузчик является самым нижним уровнем и представляет собой часть самой JVM. Он загружает классы из папки rt.jar (в которой содержатся основные классы Java) и других системных расширений.

2. Загрузчик расширений (Extension Class Loader): Этот загрузчик загружает классы из папки jre/lib/ext, которая содержит классы для расширения функциональности JVM.

3. Загрузчик приложений (System/ Application Class Loader): Этот загрузчик загружает классы из указанных в переменной окружения CLASSPATH путей и папок, а также из текущего рабочего каталога приложения.

4. Пользовательский загрузчик классов (Custom Class Loader): Этот загрузчик может быть создан программистом для загрузки классов из нестандартных мест, например, из сети или базы данных.

Классы загружаются по требованию, когда они впервые используются в программе. После загрузки класс становится доступен для инициализации и выполнения методов.

Таким образом, загрузчик классов является не программой в обычном смысле, а встроенным компонентом JVM, отвечающим за динамическую загрузку классов во время выполнения программы.

Загрузчик классов является частью JRE, которая динамически загружает Java классы в JVM.

Обычно классы загружаются только по запросу. Система исполнения в Java не должна знать о файлах и файловых системах благодаря загрузчику классов. Делегирование является важной концепцией, которую выполняет загрузчик.

Загрузчик классов отвечает за поиск библиотек, чтение их содержимого и загрузку классов, содержащихся в библиотеках. Эта загрузка обычно выполняется «по требованию», поскольку она не происходит до тех пор, пока программа не вызовет класс. Класс с именем может быть загружен только один раз данным загрузчиком классов.

При запуске JVM, используются три загрузчика классов:

+ Bootstrap class loader (Загрузчик класса Bootstrap)
+ Extensions class loader (Загрузчик класса расширений)
+ System class loader (Системный загрузчик классов)

Загрузчик класса Bootstrap - загружает основные библиотеки Java, расположенные в папке <JAVA_HOME>/jre/lib. Этот загрузчик является частью ядра JVM, написан на нативном коде.

Загрузчик класса расширений - загружает код в каталоги расширений. <JAVA_HOME>/jre/lib/ext, или любой другой каталог, указанный системным свойством java.ext.dirs.

Системный загрузчик - загружает код, найденный в java.class.path, который сопоставляется с переменной среды CLASSPATH. Это реализуется классом sun.misc.Launcher$AppClassLoader.

Загрузчик классов выполняет три основных действия в строгом порядке:

+ Загрузка: находит и импортирует двоичные данные для типа.
+ Связывание: выполняет проверку, подготовку и (необязательно) разрешение.
  - Проверка: обеспечивает правильность импортируемого типа.
  - Подготовка: выделяет память для переменных класса и инициализация памяти значениями по умолчанию.
  - Разрешение: преобразует символические ссылки из типа в прямые ссылки.
+ Инициализация: вызывает код Java, который инициализирует переменные класса их правильными начальными значениями.
  
**Пользовательский загрузчик классов**

Загрузчик классов написан на Java. Поэтому возможно создать свой собственный загрузчик классов, не понимая тонких деталей JVM. У каждого загрузчика классов Java есть родительский загрузчик классов, определенный при создании экземпляра нового загрузчика классов или в качестве системного загрузчика классов по умолчанию для виртуальной машины.

Что делает возможным следующее:

+ загружать или выгружать классы во время выполнения (например, динамически загружать библиотеки во время выполнения, даже из ресурса HTTP). Это важная особенность для:
  - реализации скриптовых языков;
  - использования bean builders;
  - добавления пользовательского расширения;
  - позволения нескольким пространствам имен общаться.
    
    <sub>Например, это одна из основ протоколов CORBA / RMI;</sub>
+ изменить способ загрузки байт-кода
  
<sub>Например, можно использовать зашифрованный байт-код класса Java;</sub>
+ модифицировать загруженный байт-код
  
<sub>Например, для переплетения аспектов во время загрузки при использовании аспектно-ориентированного программирования;</sub>

[к оглавлению](#java)

## Что такое JIT?

JIT-компиляция (англ. Just-in-time compilation, компиляция «на лету»), динамическая компиляция (англ. dynamic translation) - технология увеличения производительности программных систем, использующих байт-код, путём компиляции байт-кода в машинный код или в другой формат непосредственно во время работы программы.

JIT означает Just In Time, то есть "точно вовремя". JIT-компиляция транслирует байт-код виртуальной машины в машинный код физической машины именно в тот момент, когда он требуется в первый раз. (Это в частности значит, что если метод ни разу не вызывался за время работы программы, он не транслируется.).
Метод, единожды скомпилированный, остаётся в памяти (кешируется) и при последующих вызовах выполняется сразу.

[к оглавлению](#java)

## Что такое сборщик мусора?

+ [Статья habr - Избавляемся от мусора в Java](https://habr.com/ru/companies/otus/articles/553996/)

+ [Статья Хабр - Управление памятью в Java](https://habr.com/ru/articles/549176/)

+ [Статья Javarush - про сбозик мусора, ссылки и т.п.](https://javarush.com/groups/posts/2689-uchimsja-guglitjh--4-urovenjh--11-lekcija)

+ [YouTube - Разбираем Garbage Collector в Java](https://www.youtube.com/watch?v=PA8z44ludgc&list=WL&index=37&t=1203s)

+ [Статья на Хабр - про мягкие ссылки](https://habr.com/ru/articles/169883/)

> Способ автоматического управления памятью.

Сборщик мусора (Garbage Collector) должен делать всего две вещи:

+ Находить мусор - неиспользуемые объекты.
Объект считается неиспользуемым, если ни одна из сущностей в коде, выполняемом в данный момент, не содержит ссылок на него, либо цепочка ссылок, которая могла бы связать объект с некоторой сущностью приложения, обрывается.

+ Освобождать память от мусора.
Работа сборщика мусора не бесплатная, она оплачивается ресурсами компьютера и задержками в выполнении программы.

### `Обнаружение мусора`

Существует два подхода к обнаружению мусора:

+ Reference counting;
+ Tracing;

*Reference counting (подсчёт ссылок).*

Суть этого подхода состоит в том, что каждый объект имеет счетчик. Счетчик хранит информацию о том, сколько ссылок указывает на объект. Когда ссылка уничтожается, счетчик уменьшается. Если значение счетчика равно нулю - объект можно считать мусором.

Главным минусом такого подхода является сложность обеспечения точности счетчика. Также при таком подходе сложно выявлять циклические зависимости (когда два объекта указывают друг на друга, но ни один живой объект на них не ссылается), что приводит к утечкам памяти.

*Tracing (трассировка)*

- живыми могут считаться только те объекты, до которых мы можем добраться из корневых точек (GC Root) и те объекты, которые доступны с живого объекта. Всё остальное - мусор.

Существует 4 типа корневых точки:

+ Локальные переменные и параметры методов;
+ Потоки;
+ Статические переменные;
+ Ссылки из JNI.
  
Самое простое java приложение будет иметь корневые точки:

+ Локальные переменные внутри main() метода и параметры main() метода;
+ Поток который выполняет main();
+ Статические переменные класса, внутри которого находится main() метод.
  
Таким образом, если мы представим все объекты и ссылки между ними как дерево, то нам нужно будет пройти с корневых узлов (точек) по всем рёбрам. При этом узлы, до которых мы сможем добраться - не мусор, все остальные - мусор. При таком подходе циклические зависимости легко выявляются. HotSpot VM использует именно такой подход.

### `Очистка от мусора`

Для очистки памяти от мусора существуют два основных метода:

+ Copying collectors
+ Mark-and-sweep
  
При **Copying collectors подходе** память делится на две части «from-space» и «to-space», при этом сам принцип работы такой:

+ Объекты создаются в «from-space»;
+ Когда «from-space» заполняется, приложение приостанавливается;
+ Запускается сборщик мусора. Находятся живые объекты в «from-space» и копируются в «to-space»;
+ Когда все объекты скопированы «from-space» полностью очищается;
+ «to-space» и «from-space» меняются местами.
  
Главный плюс такого подхода в том, что объекты плотно забивают память.

Минусы подхода:

+ Приложение должно быть остановлено на время, необходимое для полного прохождения цикла сборки мусора;
+ В худшем случае (когда все объекты живые) «form-space» и «to-space» будут обязаны быть одинакового размера.
  
Алгоритм работы **mark-and-sweep** можно описать так:

+ Объекты создаются в памяти;
+ В момент, когда нужно запустить сборщик мусора приложение приостанавливается;
+ Сборщик проходится по дереву объектов, помечая живые объекты;
+ Сборщик проходится по всей памяти, находя все не отмеченные куски памяти и сохраняя их в «free list»;
+ Когда новые объекты начинают создаваться они создаются в памяти доступной во «free list».
  
Минусы этого способа:

+ Приложение не работает пока происходит сборка мусора;
+ Время остановки напрямую зависит от размеров памяти и количества объектов;
+ Если не использовать «compacting» память будет использоваться не эффективно.

### `Сборщики мусора HotSpot VM`

Они используют комбинированный подход Generational Garbage Collection , который позволяет использовать разные алгоритмы для разных этапов сборки мусора.

Этот подход опирается на том, что:

+ большинство создаваемых объектов быстро становятся мусором;
+ существует мало связей между объектами, которые были созданы в прошлом и только что созданными объектами.

Сборщик мусора (Garbage Collector) - это часть виртуальной машины Java (JVM), которая автоматически управляет памятью и освобождает объекты, которые больше не используются в программе. Он отслеживает объекты, которые больше не доступны для программы и освобождает занимаемую ими память, чтобы она могла быть использована для других целей.

Когда объект создается в Java, память выделяется для его хранения. В процессе выполнения программы объекты могут становиться недоступными, например, когда переменная, указывающая на объект, перестает ссылаться на него. В таких случаях сборщик мусора обнаруживает эти недоступные объекты и автоматически освобождает память, которую они занимали.

Сборщик мусора выполняет следующие основные задачи:

1. Определение недоступных объектов: Сборщик мусора определяет объекты, на которые нет ссылок из активной части программы. Это могут быть объекты, на которые ссылки были утеряны или которые больше не используются.

2. Освобождение памяти: После определения недоступных объектов, сборщик мусора освобождает память, занимаемую этими объектами. Он возвращает эту память обратно в пул памяти, чтобы она могла быть использована для создания новых объектов.

3. Устранение утечек памяти: Сборщик мусора помогает предотвратить утечки памяти, которые могут возникать, когда объекты не были явно освобождены программистом. Он автоматически освобождает память, занимаемую недоступными объектами, даже если программист забыл освободить их.

Сборка мусора является одной из ключевых особенностей Java, которая облегчает разработку программ, освобождая программиста от ручного управления памятью. Однако, хотя сборка мусора автоматическая, она может вызывать небольшую паузу в работе программы, когда выполняется процесс сборки мусора. В большинстве случаев, сборка мусора в Java работает эффективно и не требует вмешательства программиста.

### `Как работает сборщик мусора?`

Механизм сборки мусора - это процесс освобождения места в куче, для возможности добавления новых объектов.

Объекты создаются посредством оператора new , тем самым присваивая объекту ссылку.

Для окончания работы с объектом достаточно просто перестать на него ссылаться, например, присвоив переменной ссылку на другой объект или значение null. Так же можно прекратить выполнение метода, чтобы его локальные переменные завершили свое существование естественным образом.

Объекты, на которые отсутствуют ссылки, принято называть мусором (garbage), который будет удален.

Виртуальная машина Java, применяя механизм сборки мусора, гарантирует, что любой объект, обладающий ссылками, остается в памяти — все объекты, которые недостижимы из исполняемого кода, ввиду отсутствия ссылок на них, удаляются с высвобождением отведенной для них памяти. Точнее говоря, объект не попадает в сферу действия процесса сборки мусора, если он достижим посредством цепочки ссылок, начиная с корневой (GC Root) ссылки, т.е. ссылки, непосредственно существующей в выполняемом коде.

Память освобождается сборщиком мусора по его собственному «усмотрению». Программа может успешно завершить работу, не исчерпав ресурсов свободной памяти или даже не приблизившись к этой черте и поэтому ей так и не потребуются «услуги» сборщика мусора.

Мусор собирается системой автоматически, без вмешательства пользователя или программиста, но это не значит, что этот процесс не требует внимания вовсе. Необходимость создания и удаления большого количества объектов существенным образом сказывается на производительности приложений и если быстродействие программы является важным фактором, следует тщательно обдумывать решения, связанные с созданием объектов, — это, в свою очередь, уменьшит и объем мусора, подлежащего утилизации.

### `Какие разновидности сборщиков мусора реализованы в виртуальной машине HotSpot?`

Java HotSpot VM предоставляет разработчикам на выбор четыре различных сборщика мусора:

+ Serial (последовательный) — самый простой вариант для приложений с небольшим объемом данных и не требовательных к задержкам. На данный момент используется сравнительно редко, но на слабых компьютерах может быть выбран виртуальной машиной в качестве сборщика по умолчанию.

Использование Serial GC включается опцией:

-XX:+UseSerialGC

+ Parallel (параллельный) — наследует подходы к сборке от последовательного сборщика, но добавляет параллелизм в некоторые операции, а также возможности по автоматической подстройке под требуемые параметры производительности.

Параллельный сборщик включается опцией:

-XX:+UseParallelGC

+ Concurrent Mark Sweep (CMS) — нацелен на снижение максимальных задержек путем выполнения части работ по сборке мусора параллельно с основными потоками приложения. Подходит для работы с относительно большими объемами данных в памяти.

Использование CMS GC включается опцией:

-XX:+UseConcMarkSweepGC

+ Garbage-First (G1) — создан для замены CMS, особенно в серверных приложениях, работающих на многопроцессорных серверах и оперирующих большими объемами данных.

G1 включается опцией Java:

-XX:+UseG1GC

[к оглавлению](#java)

# Что такое Heap и Stack память в Java? Чем они отличаются?

Heap (куча) используется Java Runtime для выделения памяти под объекты и классы.

Создание нового объекта также происходит в куче. Это же является областью работы сборщика мусора. Любой объект, созданный в куче, имеет глобальный доступ и на него могут ссылаться из любой части приложения.

Stack (стек) это область хранения данных также находящееся в общей оперативной памяти (RAM) только для одного потока.

Всякий раз, когда вызывается метод, в памяти стека создается новый блок, который содержит примитивы и ссылки на другие объекты в методе. Как только метод заканчивает работу, блок также перестает использоваться, тем самым предоставляя доступ для следующего метода. Размер стековой памяти намного меньше объема памяти в куче. Стек в Java работает по схеме LIFO (Последний-зашел-Первый-вышел)

**Различия между Heap и Stack**

+ Куча используется всеми частями приложения в то время как стек используется только одним потоком исполнения программы.
+ Всякий раз, когда создается объект, он всегда хранится в куче, а в памяти стека содержится лишь ссылка на него. Память стека содержит только локальные переменные примитивных типов и ссылки на объекты в куче.
+ Объекты в куче доступны с любой точке программы, в то время как стековая память не может быть доступна для других потоков, только для одного потока.
+ Стековая память существует лишь какое-то время работы программы, а память в куче живет с самого начала до конца работы программы.
+ Если память стека полностью занята, то Java Runtime бросает исключение:

`java.lang.StackOverflowError`

Если заполнена память кучи, то бросается исключение:

`java.lang.OutOfMemoryError: Java Heap Space`

+ Размер памяти стека намного меньше памяти в куче.
+ Из-за простоты распределения памяти, стековая память работает намного быстрее кучи.
  
Для определения начального и максимального размера памяти в куче используются -Xms и -Xmx опции JVM. Для стека определить размер памяти можно с помощью опции -Xss. Размер стека задаётся при создании потока, и у каждой переменной есть максимальный размер, зависящий от типа данных, размер кучи ограничен оперативной памятью.

**Верно ли утверждение, что примитивные типы данных всегда хранятся в стеке, а экземпляры ссылочных типов данных в куче?**  
Не совсем. Примитивное поле экземпляра класса хранится не в стеке, а в куче. Любой объект (всё, что явно или неявно создаётся при помощи оператора new) хранится в куче.

**Каким образом передаются переменные в методы, по значению или по ссылке?**  
В Java параметры всегда передаются только по значению, что определяется как «скопировать значение и передать копию». С примитивами это будет копия содержимого. Со ссылками - тоже копия содержимого, т.е. копия ссылки. При этом внутренние члены ссылочных типов через такую копию изменить возможно, а вот саму ссылку, указывающую на экземпляр - нет.

[к оглавлению](#java)
