### Оглавление

1. [Apach Maven - описание](#apach-maven)
2. [Apach Maven - установка](#apach-maven-установка)
3. [Java Development Kit](#java-development-kit)
4. [IntelliJ IDEA](#intellij-idea)

___
## Apach Maven
**Maven** - самый популярный инструмент сборки в пространстве Java, в то время как интеграционное тестирование является неотъемлемой частью процесса разработки. Поэтому естественным выбором является настройка и выполнение интеграционных тестов с помощью Maven.

Зачем усложнять себе жизнь и осваивать еще один IT-инструмент? А он оказывается наоборот - облегчает рабочий процесс тем, кто занимается IT масштабно!

Когда вы работаете над конкретным проектом Java, и у этого проекта много зависимостей, сборок, требований, то работа со всеми этими вещами **вручную** является чрезвычайно сложной и трудоемкой. Таким образом, использование некоторых инструментов, которые **могут выполнить** эти работы, действительно полезно.

А **Maven** - это такой инструмент управления сборкой, который может выполнять все такие вещи, как добавление зависимостей, использование пути к классам для проецирования, автоматическое создание файлов war и jar и много других вещей. Сейчас обо всём поподробнее.

Функциональность системы сборки Maven шире, чем компилятора исходного кода. В процессе работы приложения Apache Maven **вызывает** компилятор и при этом **автоматически управляет** зависимостями и ресурсами, например:

- загружает подходящие версии пакетов;
- размещает изображения, аудио- и видеофайлы в нужных папках;
- подгружает сторонние библиотеки.

Автоматическая сборка приложения особенно важна на этапах разработки, отладки и тестирования — Maven помогает собрать код и ресурсы в исполняемое приложение без IDE (среды разработки). При этом система сборки отличается гибкостью:

- может использоваться в IDE — Eclipse, IntelliJ IDEA, NetBeans и других;
- не зависит от операционной системы;
- не требует установки — архив с программой можно распаковать в любой директории;
- все необходимые параметры имеют оптимальные настройки по умолчанию;
- упрощает организацию командной работы и документирование;
- запускает библиотеки для модульного тестирования;
- обеспечивает соблюдение стандартов;
- имеет огромное количество плагинов и расширений.

### Жизненный цикл Maven
Maven выполняет сборку последовательными фазами. Названия на английском, так как они используются в качестве команд.

1. Проверка — validate. Фреймворк проверяет, корректен ли проект и предоставлена ли вся необходимая для сборки информация.
2. Компиляция — compile. Maven компилирует исходники проекта.
3. Тест — test. Проверка скомпилированных файлов. В нашем случае будет использована библиотека JUnit.
4. Сборка проекта — package. По умолчанию осуществляется в формате JAR. Этот параметр можно изменить, добавив в project тег packaging.
5. Интеграционное тестирование — integration-test. Maven обрабатывает и при необходимости распаковывает пакет в среду, где будут выполняться интеграционные тесты.
6. Верификация — verify. Артефакт проверяется на соответствие критериям качества.
7. Инсталляция — install. Артефакт попадает в локальный репозиторий. Теперь его можно использовать в качестве зависимости.
8. Размещение проекта в удалённом репозитории — deploy, — финальная стадия работы.


Эти фазы упорядочены и выполняются поочерёдно. Если необходимо собрать проект, система последовательно проведёт оценку, компиляцию и тестирование, и только после этого сборку. Помимо этого есть две фазы, выполняющиеся отдельно, только прямой командой. Это очистка — ***clean***, удаляющая предыдущие сборки, и создание документации для сайта — ***site***.

### Какие задачи решает Maven
1. Управление зависимостями

Одной из самых выжных способностей Maven является то, что в нём присутствует система автоматического управления зависимостями. Насколько это просто? Если без использования Maven нам нужно было самим искать нужную библиотеку нужной версии где-то в интернете, скачивать её, добавлять в класс path при компиляции, то теперь для того, чтобы использовать чью-то библиотеку, нам нужно просто указать её координаты Maven, и он всё сделает сам!

2. Компиляция

Эта задача теперь также выполняется автоматически. Нам вообще не нужно писать какие-то команды в терминале, что-то указывать (какие директории нужно скомпилировать, куда положить скомпилированные ресурсы). Всё делается автоматически с использованием **принципа соглашения над конфигурацией**. 

*Принцип ***"Соглашение важнее конфигурации" (convention over configuration)*** — это принцип проектирования программного обеспечения, целью которого является уменьшение количества лишних действий, необходимых разработчику при создании своего проекта.*

*В Apache Maven данный принцип проявляется в том, что Maven предоставляет разумные настройки (готовые шаблоны) по умолчанию для управления сборкой проекта. Если они не подходят, то разработчик может переопределить их на свои.*

*Одной из таких настроек по умолчанию, например, является структура каталогов в Maven-проекте.*

Весь процесс деплоя упрощается в разы. Это всё также относится и к **выполнению тестов**.

3. Выполнение тестов

Выбор движка для тестов, настройка тестового окружения - теперь это всё выполняется автоматически при сборке, либо, если нам нужно, вызовом одной простой команды (или кнопки в IDE).

4. Сборка в архив

При использовании Maven количество действий, которые нам нужно сделать руками, очень сильно сокращается. А значит меньше вероятность допустить ошибку на каком-либо шаге и больше времени можно выделить непосредственному решению бизнесс-задач вместо выполнения команд в терминале.

5. Деплой на сервер приложений.

Если бы Maven умел делать только вышеперчисленные пункты, то уже это было бы большим доводом его использовать. На самом деле Maven умеет намного больше, чем автоматизированная система сборки, и преимущества его использования не ограничиваются только упрощением процесса сборки проекта, хотя это тоже немало.

### Другие задачи, которые решает Maven
Большим преимуществом является то, что Maven использует **унифицированный подход к сборке**.

Следовательно, если вы познакомились с **одним** Maven-проектом, то вы знаете, как работают **все остальные** Maven-проекты. Это огромное достижение, экономящее много сил, времени и нервов, потому что без унифицированной системы программисты бы использовали подход "сколько людей - столько и мнений" со всеми вытекающими последствиями. В итоге разные проекты, а точнее: сборка и деплой могли бы сильно отличаться между собой. Это конечно не очень хорошо, так как состав команд может меняться. Когда же мы используем один подход ко всем проектам, мы можем быть уверенны, что порог понимания "как нужно развернуть новый проект" будет минимальный. Это тоже последствия принципа ***"convention over configuration"***.

Также при использовании Maven:

- мы можем получить исчерпывающую информацию о таких свойствах проекта как **полное визуализированное дерево всех зависимостей проекта**, включающее в себя транзетивные зависимости. Это бывает порой необходимо для решения задач совместимости.
- кроме непосредственного прогона всех имеющихся или отдельных тестов мы также можем получить **отёт о тестировании**, в котором будет видно, например, насколько хорошо код **покрыт тестами**. Это важно для понимания того, какие части нашего приложения находятся под нашим контролем, а какие еще нет. Контролируемое приложение - это приложение протестированное!
- Maven способствует формированию хороших **программистских привычек**. При использовани стандартной структуры директории мы учимся и привыкаем к тому, например, что тестовый код должен храниться отдельно от основного но в параллельных пакетах. Кроме того наименования наших директорий должны соответствовать общепринятым. Результат - более понятная структура проекта и уменьшение затрат на разбирательство с ними.

Тем не менее это не означает, что всё обязательно должно быть только так, как описано в настройках и никак иначе. При необходимости мы всегда можем **изменить** и **настроить** проект так, как нам нужно. Например, существует механизм **плагинов** и **профилей**, который повзоляет кастомизировать сборку в соответствии с нашими задачами. Существует огромное количество плагинов под разные задачи. Но, если плагин решающий текущую задачу всё-таки не существует, то есть возможность создать **свой собственный** плагин! Профили же помогают **настроить** процесс сборки в зависимости от каких-либо условий.

___
*Материал о возможностях Maven взят из вводного урока по курсу от ITVDN и Егунова Глеба. Полная версия урока [здесь](https://www.youtube.com/watch?v=PMifgvG7KS0)*
___
### Как работает Maven?
Maven использует **объектную модель проекта (Project Object Model, POM)** для управления проектом. Для описания модели обычно используется XML-документ, но возможны и другие форматы.

[![maven.png](https://i.postimg.cc/02WMMHhV/maven.png)](https://postimg.cc/kBSXLwJS)

### Что такое Объектная модель проекта (POM)?

POM — это очень полезная и удобная вещь, которая описывает то, как будет собираться проект. Этот файл (обычно pom.xml) состоит из следующих частей:
- **Project coordinates (координаты проекта)** — однозначно идентифицируемый набор свойств, с помощью которых артефакты проекта могут быть использованы в другом месте
- **Dependencies (зависимости)** — библиотеки и код, необходимые для сборки проекта
- **Plugins (плагины)** — вспомогательные инструменты при сборке проекта
- **Properties (свойства)** — общие значения, необходимые проекту
- **Inheritance details (детали наследования)** — возможность создания иерархии для повторно используемых компонентов POM
- **Profiles (профили)** — альтернативные пути сборки проекта, разбитые по профилям
 
**Как Maven взаимодействует с POM?**
Maven использует содержимое в POM для управления сборкой. Однако он также имеет стандартные значения по умолчанию. Таким образом, Maven несет ответственность за объединение значений по умолчанию и применение переопределений и дополнений, обнаруженных в pom-файле проекта.

Благодаря этому мы получаем:
- совокупность шагов выполнения, свойств и профилей
- контент, который Maven может выполнить для проекта
- исчерпывающий набор зависимостей и плагинов, необходимых для такого выполнения
- определение любых переходных зависимостей (например, зависимости зависимостей)
- разрешение конфликтов с точки зрения версий зависимостей

**Как Maven собирает POM?**

[![maveneffectivepom.webp](https://i.postimg.cc/6pCKJ8VC/maveneffectivepom.webp)](https://postimg.cc/yD6t0YbN)

Maven собирает свой POM, проходя слои, которые действуют как строительные блоки. Каждый используемый слой имеет возможность переопределять или дополнять содержимое того, что станет POM. Родительские файлы, спецификации и файлы POM-проекта — это то, где можно переопределить настройки Maven по умолчанию.

*Полный текст статьи об основах Maven на [TopJava.ru](https://topjava.ru/blog/apache-maven-osnovy-1)*

⬆️[Оглавление](#оглавление)
___
## Apach Maven. Установка
(для Windows)

1. Чтобы установить Maven необходимо:

✅ перейти на [официальный сайт](https://maven.apache.org/)

✅ выбрать раздел **Download**

✅ скачать на компьютер файл для установки. Самый простой вариант - Binary zip archive (чистый Maven без плагинов)

✅ распаковать в любую удобную директорию
  
[![Maven-1.png](https://i.postimg.cc/vZLThv7Z/Maven-1.png)](https://postimg.cc/qNqpMyZP)
\
\
2. Следующим шагом нужно добавить **системную переменную Path** - путь до папки **bin** в директории, куда мы установили Maven. Для этого:

✅ находим папку **bin** в папке с рапакованным Maven

[![Maven-2.png](https://i.postimg.cc/HWcH1SQn/Maven-2.png)](https://postimg.cc/RqB2cLpx)
\
\
✅ заходим в папку **bin** и копируем весь путь к это папке

[![Maven-3.png](https://i.postimg.cc/Y9cVKwYz/Maven-3.png)](https://postimg.cc/wtVFLZW1)
\
\
✅ для Windows 11 (моя версия) заходим в главное меню **Пуск** (на всякий случай добавлю и этот скриншот 😏)

[![Maven-4.png](https://i.postimg.cc/8cHHs23W/Maven-4.png)](https://postimg.cc/m1PM55T2)
\
\
✅ в раскрывшемся окне заходим в **Параметры**

[![Maven-5.png](https://i.postimg.cc/zfTRJ9Vk/Maven-5.png)](https://postimg.cc/GBhpKgPB)
\
\
✅ в разделе **Система** заходим в подраздел **О системе**

[![Maven-6.png](https://i.postimg.cc/pX9SsZ9H/Maven-6.png)](https://postimg.cc/fJN5LYj2)
\
\
✅ выбираем **Дополнительные параметры системы**

[![Maven-7.png](https://i.postimg.cc/zGp8r7kc/Maven-7.png)](https://postimg.cc/FYf2bj8y)

✅ в появившемся меню нажимаем на **Переменные среды** в самом низу окна

[![Maven-8.jpg](https://i.postimg.cc/Yq6m1cpL/Maven-8.jpg)](https://postimg.cc/rKpmkPRq)
\
\
✅ в нижнем окошке **Системные переменные** находим переменную **Path**, нажимаем на неё и на кнопку **Изменить**

[![Maven-9.jpg](https://i.postimg.cc/g234Xt7g/Maven-9.jpg)](https://postimg.cc/qNM2Ww4K)
\
\
✅ в новом меню нажимаем **Создать** и вот теперь в поле ввода вставляем наш скопированный путь до папки **bin**, нажимаем **Ok** и далее тоже несколько раз **Ok** для сохранения изменений

[![Maven-10.jpg](https://i.postimg.cc/v8NcfYFm/Maven-10.jpg)](https://postimg.cc/14DmZZzx)
\
\
3. Для корректной работы с Maven на вашем компьютере должна быть установлена **Java**, так как Maven использует её для своей работы. Поэтому в следующем разделе я покажу **установку** Java.

⬆️[Оглавление](#оглавление)
___
## Java Development Kit



⬆️[Оглавление](#оглавление)
___
## IntelliJ IDEA


⬆️[Оглавление](#оглавление)
