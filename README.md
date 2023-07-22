### Оглавление

1. [Apach Maven - описание](#apach-maven-описание)
2. [Apach Maven - установка](#apach-maven-установка)
3. [Java Development Kit](#java-development-kit)
4. [IntelliJ IDEA](#intellij-idea)

___
## Apach Maven - описание
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

### Основные возможности Maven
- Наиболее важные возможности Maven:
- Простая настройка проекта в соответствии с лучшими практиками
- Управление зависимостями, включая автоматическое обновление
- Возможность работать с несколькими проектами одновременно
- Большое хранилище библиотек и метаданных для использования «из коробки»
- Расширяемость с возможностью написания своих плагинов
- Создание сайта и PDF с документацией
- Проверка корректности структуры проекта
- Компиляция исходного кода, отображение ошибок/предупреждений
- Тестирование проекта на основе уже написанных тестов
- Упаковка скомпилированного кода в артефакты (например, .jar, .war, .ear, .zip-архивы и многое другое)
- Упаковка исходного кода в загружаемые архивы/артефакты
- Установка упакованных артефактов на сервер для последующего развертывания (деплоя) или в репозиторий для распространения
- Создание отчетов по тестированию
- Сообщение об удачной/неудачной сборке проекта

### Принцип "Соглашение важнее конфигурации"
Соглашение важнее конфигурации — это принцип проектирования программного обеспечения, целью которого является уменьшение количества лишних действий, необходимых разработчику при создании своего проекта.

В Apache Maven данный принцип проявляется в том, что Maven предоставляет разумные настройки (готовые шаблоны) по умолчанию для управления сборкой проекта. Если они не подходят, то разработчик может переопределить их на свои.

Одной из таких настроек по умолчанию, например, является структура каталогов в Maven-проекте.

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

*Полный текст статьи об основах Maven на [TopJava.ru](https://topjava.ru/blog/apache-maven-osnovy-1)

⬆️[Оглавление](#Оглавление)
___
## Java Development Kit



⬆️[Оглавление](#Оглавление)
___
## IntelliJ IDEA


⬆️[Оглавление](#Оглавление)
