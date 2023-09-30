### Оглавление

1. [Apach Maven - описание](#apach-maven)
2. [Apach Maven - установка](#apach-maven-установка)
3. [Java Development Kit](#java-development-kit)
4. [IntelliJ IDEA](#intellij-idea)
5. [Создание проекта под управлением Maven](#Создание-проекта-под-управлением-Maven)

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

[![Maven-6.png](https://i.postimg.cc/hvqN6ngF/Maven-6.png)](https://postimg.cc/phq05gpk)
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
1. Для установки Java открываем сайт www.oracle.com и заходим в раздел **Products**

[![Java-1.png](https://i.postimg.cc/d1DPPFhD/Java-1.png)](https://postimg.cc/sQF07t9R)
\
\
2. В нижнем левом углу выбираем **Java**


[![Java-2.png](https://i.postimg.cc/yxytWq1C/Java-2.png)](https://postimg.cc/RJqXbDJg)

\
\
3. В верхнем правом углу выбираем **Download Java**

[![Java-3.png](https://i.postimg.cc/CxFwPWsn/Java-3.png)](https://postimg.cc/bsBXdVMq)
\
\
4. Выбираем нужную версию Java, операционной системы и файла для скачиваения

[![Java-4.png](https://i.postimg.cc/7ZsrBbLj/Java-4.png)](https://postimg.cc/WdkyzNg7)
\
\
Установка у Java стандартная, просто действуем, следуя инструкции.
\
\
5. Давайте проверим, что Java и Maven установились корректно. Для этого в командной строке ввёдем по-очереди команды:

```
java -version
```
и 

```
maven -version
```

\
Если всё получилось, Windows покажет информацию об установленных версиях Java и Maven. 
В противном случае будет информация о том, что один из них (или оба) не является командой или программой.


[![Maven-11.png](https://i.postimg.cc/DyY4HShL/Maven-11.png)](https://postimg.cc/VdnNbLdk)

\
\
⬆️[Оглавление](#оглавление)
___
## IntelliJ IDEA
Для работы нам потребуется удобная среда разработки. Изначально Maven создавался для работы в командной строке, по этой причине и было сокращено его название для командной строки до **mvn**.
Но после появления сред разработки удобнее конечно стало работать в них. Сред разработки много разных, но мы рассмотрим самую популярную - **IntelliJ IDEA**
___
IntelliJ IDEA - это IDE, интегрированная среда разработки (комплекс программных средств, который используется для написания, исполнения, отладки и оптимизации кода) для Java, JavaScript, Python и других языков программирования от компании JetBrains. Отличается обширным набором инструментов для рефакторинга (перепроектирования) и оптимизации кода.
___
1. Для установки IntelliJ IDEA на Windows надо зайти на официальный сайт [Jetbrains](https://www.jetbrains.com)

[![Idea-1.png](https://i.postimg.cc/3w0GRKDW/Idea-1.png)](https://postimg.cc/7CDhtr9y)

Выбрать во вкладке **Developer Tools** IntelliJ IDEA

[![Idea-2.png](https://i.postimg.cc/25jzcTCY/Idea-2.png)](https://postimg.cc/Sn5Fj6X1)

И нажать **Download** для загрузки установщика

[![Idea-3.png](https://i.postimg.cc/j5wYmF9p/Idea-3.png)](https://postimg.cc/ygHGSv7j)

Либо сразу перейти по [этой ссылке](https://www.jetbrains.com/idea/download/?section=windows). В любом случае придёте куда надо)

2. Далее надо выбрать какую версию Idea надо загрузить и в каком формате.

Если вы работаете и в вашей компании нужна версия **Ultimate**, то думаю вам об этом уже сообщили, иначе нам она не нужна.
[![Idea-4.png](https://i.postimg.cc/tTX2VZd2/Idea-4.png)](https://postimg.cc/VSVjxNVC)

**Версия Ultimate** - профессиональная платная версия. Предназначена для фулстек-разработки и создания корпоративных приложений. Поддерживает широкий набор фреймворков и технологий для бэкенда и фронтенда и включает инструменты для профилирования и работы с базами данных, HTTP-клиент и много других функций. Все возможности пакета можно протестировать бесплатно в течение 30 дней, а при оформлении заявки на командное тестирование — в течение 90 дней. Потом вам придётся заплатить минимум 533 доллара США.

Нам же нужна версия **Community Edition**. 

Это бесплатный вариант для личного и коммерческого использования. Функциональность, по сравнению с версией Ultimate, значительно урезана: нет встроенного HTTP-клиента, отсутствуют инструменты для работы с базами данных, не поддерживаются совместная работа и удаленный доступ. Тме не менее нам её достаточно.

Выбираем нужный нам формат (рекомендую .exe) и загружаем через **download**

[![Idea-5.png](https://i.postimg.cc/j57P2RmZ/Idea-5.png)](https://postimg.cc/xJ9cFV0z)

3. Устанавливаем Idea. Зупускаем установщик. Установка стандартная.

В процессе установки можете выбрать в этом окне:
- размещение ярлыка на рабочем столе
- в разделе "Сreate associations" выбрать .java - это свяжет файлы с IDE в системе: когда вы будете нажимать на файлы с этим расширением в вашем файловом менеджере (проводнике Windows), они будут открываться в IDE.

[![Idea-6.jpg](https://i.postimg.cc/G2RR6QFz/Idea-6.jpg)](https://postimg.cc/gwg1Z3B6)

4. После окончания процесса установки вы можете просто завершить установку, нажав **Finish**. Но я рекомендую перед этим поставить галочку для запуска Idea сразу.

При первом запуске IntelliJ IDEA перед вами выскочит диалоговое окно с требованием указать путь до файла с настройками. Так как это наш первый опыт знакомства с IDE, то выбираем пункт **Do not import settings**. Если данное окно вылезло после обновления или переустановки – выберите исходную директорию.

[![Idea-7.png](https://i.postimg.cc/J7bKQW49/Idea-7.png)](https://postimg.cc/XXYwVm58)

Далее откроется следующее окно, из которого мы сразу можем создать новый проект.

[![Idea-8.png](https://i.postimg.cc/hvjLnNT0/Idea-8.png)](https://postimg.cc/R6k6QsP3)

В разделе **Customize** можно выбрать тему оформления, размер шрифта (IDE font):

[![Idea-9.png](https://i.postimg.cc/rm8yYrtB/Idea-9.png)](https://postimg.cc/McF8nX55)


⬆️[Оглавление](#оглавление)
___
## Создание проекта под управлением Maven
Теперь попробуем создать наш первый тестовый проект под управлением Maven. Для этого в Idea на главном экране выберем **Create new project**. Откроется окно с настройкой конфигураций нового проекта:

[![Maven-project-1.png](https://i.postimg.cc/B6ghW4hM/Maven-project-1.png)](https://postimg.cc/mzP3CfWH)

Нас интересует вкладка **Maven Archetype**
Архетип в Maven — это шаблон нового проекта, со структурой и заготовками исходных и конфигурационных файлов. Далее:

- Придумываем название проекта на латинице, если несколько слов, то пишем их через дефис или нижнее подчёркивание.
- Если надо, меняем расположение проекта. Можно оставить по умолчанию
- Если версия JDK уже стоит - замечательно, иначе смотрите в отдельном репо про Java, как её установить
- Выбираем **Catalog**. Предлагаю оставить по умолчанию - internal
___
Каталог определяется URL'ом, где он расположен, кроме того в Maven есть три предопределенных каталога internal, remote и local:

**internal**	содержит архетипы, встроенные в maven, их немного и они уже де-факто идут с самим дистрибутивом

**remote**	центральный каталог maven, находится по адресу http://repo1.maven.org/maven2/archetype-catalog.xml, его местоположение зависит от текущих настроек Maven, например возможно переопределить этот url на одно из зеркал репозитория

**local**	каталог из локального репозитория, обычно находится в ~/.m2/archetype-catalog.xml
___
- Выбираем ахретип **quickstart** (он используется, если мы хотиим создать простоe приложение)
- Нажимаем **Create** после чего Maven сделает первую сборку нашего проекта

Скорее всего после сообщения об успешной сборке проекта мы также увидим и предупреждения (WARNINGS) о том, что используется старый плагин Maven.

[![Maven-project-2.png](https://i.postimg.cc/CxM0SB1V/Maven-project-2.png)](https://postimg.cc/gn7QK08M)

Не пугаемся, это не ошибка, а всего лишь предупреждение. Но тем не менее меры для дальнейшей работы лучше предпринять.

Заходим в настройки (шестерёнку) в правом верхнем углу, еще раз нажимаем на "settings". В поисковой строке пишем "maven" нажимаем в получившемся списке на Maven.

[![Maven-project-3.png](https://i.postimg.cc/0QDFpPQf/Maven-project-3.png)](https://postimg.cc/HcW6mGbc)

[![Maven-project-4.png](https://i.postimg.cc/RZwt5YNY/Maven-project-4.png)](https://postimg.cc/nXcrq0KK)

В **Maven home path**, который обозначает путь к Maven, мы видим версию, которую использует Idea. Под строкой - собственно номер версии. Мы же себе устанавливали более новую версию.
Поэтому сейчас нажимаем на три точки справа от пути, находим куда мы устанавливали Maven, выбираем файл, т.о. прописываем новый путь до Maven и нажимаем **ОК**. 

[![Maven-project-5.png](https://i.postimg.cc/bv3sqf8m/Maven-project-5.png)](https://postimg.cc/1gV9KT8F)

[![Maven-project-6.png](https://i.postimg.cc/9Mk0qPDT/Maven-project-6.png)](https://postimg.cc/bDQp7tHN)

Убеждаемся, что версия под строкой пути поменялась на новую, нажимаем **Apply** > **OK** и смело закрываем окно. Теперь можем дальше работать с проектом.
___
Давайте познакомимся со структурой проекта, которую мы можем найти на левой панели.

- Разворачиваем название нашего проекта
- Раскрываем папку **src**, далее папку **main**
- Находим папку **Java** и в этой папке рассмотрим содержание файла App.java

[![Maven-project-8.png](https://i.postimg.cc/QMwkj7j4/Maven-project-8.png)](https://postimg.cc/kVNtcB6K)

Здесь расположен класс, который называется **App** (application), внутри которого находится метод **main**. Давайте попробуем его запустить. Для этого нажмите на зелёную стрелку слева от метода.

Скорее всего вы столкнётесь с подобной ошибкой, которую мы сейчас решим и сэкономим кучу ваших будущих часов размышлений на тему "что не так в моём проекте"!

[![Maven-project-7.png](https://i.postimg.cc/g29WLSNm/Maven-project-7.png)](https://postimg.cc/6yhSDhkm)

А дело всё в том, что мы используем на своём проекте **Java версии 20**, она на время написания мною статьи новая, а по умолчанию используется **Java версии 7** (либо 1.7, что одно и тоже)!!!

Чтобы это исправить, нужно:
- зайти в файл **pom.xml**
- найти секцию **properties**
- вставить туда (смотрите внимательно скриншот) две строчки, в которых указываете свою используемую версию Java (у меня 20):

```Java
<maven.compiler.source>20</maven.compiler.source>
<maven.compiler.target>20</maven.compiler.target>
```

[![Maven-project-11.png](https://i.postimg.cc/jSL4BTf4/Maven-project-11.png)](https://postimg.cc/68xZGDY8)

- далее в левой панели на файле **pom.xml** нажимаем ПКМ и выбираем Maven > Reload Project

[![Maven-project-9.png](https://i.postimg.cc/Sx46sqF4/Maven-project-9.png)](https://postimg.cc/QH6942dY)

Таким образом мы говорим Maven, что надо заново просканировать pom.xml, посмотреть какие изменения в нём произошли и собственно обновить наш проект.

Снова идём в **App.java**, запускаем метод **main** и, если всё хорошо, то в консоли мы увидим **Hello world!**

[![Maven-project-10.png](https://i.postimg.cc/KYvtPN8s/Maven-project-10.png)](https://postimg.cc/182gPD6p)
