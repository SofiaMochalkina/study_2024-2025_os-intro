---
## Front matter
title: "Система управления пакетами Chocolatey"
subtitle: "Реферат"
author: "Мочалкина Софья Васильевна"
## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Chocolatey — система управления пакетами для Windows

`Chocolatey` — система управления пакетами для Windows с интерфейсом командной строки и установщиком программного обеспечения на машинном уровне.

Она использует инфраструктуру упаковки NuGet и Windows PowerShell для упрощения процесса загрузки и установки программного обеспечения. 

# Основная черта Chocolatey
Основная черта Chocolatey — пакеты чаще всего не содержат установочных файлов (setup.msi, setup.exe и т. д.). В пакете находится скрипт-установщик на powershell, который скачивает и устанавливает нужную версию установочного файла из нужного места в интернете. 

Chocolatey нужен для удобного управления программами в Windows. Он делает установку, удаление и обновление программ в операционной системе похожими на те, что используются в Linux. 

# История создания

Chocolatey был создан Робом Рейнольдсом в 2011 году как простой скрипт для установки приложений из командной строки. Проект быстро набрал популярность и превратился в полноценный менеджер пакетов для Windows.

# Рост популярности

Chocolatey стал востребованным инструментом в сообществе DevOps из-за способности автоматизировать задачи управления программным обеспечением и обеспечивать согласованность в разных средах. Сегодня его используют тысячи организаций по всему миру для оптимизации процессов управления программным обеспечением.

# Открытый исходный код

Проект является открытым, что позволяет любому вносить свой вклад в его развитие. Это привело к активному сообществу разработчиков, которые помогли улучшить и расширить возможности Chocolatey.

# Использование в разных сценариях
Chocolatey применяется в различных ситуациях, от управления локальными средами разработки отдельными разработчиками до автоматизации процессов управления программным обеспечением в крупных организациях. 

# Установка Chocolatey

Во-первых, убедитесь, что вы используете административную оболочку.
Скопируйте текст, относящийся к вашей командной оболочке - cmd.exe или powershell.exe.

cmd.exe

`@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"`

PowerShell.exe

`Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`

Вставьте скопированный текст в оболочку и нажмите Enter.
Подождите несколько секунд, пока команда не будет выполнена.
Если вы не видите никаких ошибок, вы готовы использовать Chocolatey CLI!

# Самые популярные команды
`choco install <название_программы>` - установка пакета.
Ищет соответствующую программу и устанавливает её.
`choco uninstall` - удаляет указанный пакет.
`choco outdated` - показывает список устаревших установленных пакетов.
`choco upgrade <pkg|all>` - обновляет пакеты до последних версий.
Если указать all, то будут обновлены все пакеты, установленные через Chocolatey. Можно также указывать отдельные программы
`choco search <программа>` - производит поиск пакета по локальным и удалённым источникам.
`choco pin <программа>` - предотвращает обновление определённой программы.

# Основные функции
Функции:
`Установка программного обеспечения.` Chocolatey поддерживает тысячи разных программ, например Chrome, Adobe Reader, Firefox, WinRAR и Skype. 
`Обновление установленных программ.` Chocolatey проверит, требуются ли обновления, и автоматически установит новую версию. 
`Просмотр установленных пакетов.` Есть графический интерфейс для просмотра установленных пакетов, проверки обновлений и настройки параметров Chocolatey. 
`Оптимизация установки.` Команда «optimize» оптимизирует установку, сокращая использование пространства. 
Конвертация пакетов. Команда «convert» преобразует пакеты из одного типа в другой.

# Chocolatey GUI 

`Chocolatey GUI` - это графический интерфейс для инструмента Chocolatey, который позволяет устанавливать, обновлять и управлять пакетами в системе Windows. 

# Интерфейс Chocolatey GUI 
Состоит из трёх основных разделов:
`На левой стороне` — источники, где можно найти установленные в системе приложения и проверить программы, доступные в репозитории Chocolatey. 
`На верхней стороне` — панель инструментов, где можно искать пакеты и обновлять все существующие. 
`Ниже панели инструментов` — список пакетов, где можно обновлять, устанавливать, удалять и просматривать детали.

# Некоторые преимущества Chocolatey

`Простота использования.` Chocolatey упрощает установку программного обеспечения с помощью простых команд. 

`Широкий спектр пакетов.` В репозитории Chocolatey есть множество пакетов программного обеспечения, что облегчает поиск и установку различных приложений. 

`Автоматизация и создание скриптов.` Chocolatey позволяет автоматизировать задачи управления программным обеспечением с помощью скриптов, что экономит время, особенно в корпоративных средах, где нужно управлять несколькими машинами. 

`Интеграция с инструментами управления конфигурацией.` Chocolatey хорошо интегрируется с популярными инструментами управления конфигурацией, такими как Ansible, Puppet и Chef. 

`Контроль версий.` Chocolatey предоставляет возможности контроля версий, позволяя пользователям указывать, какую версию пакета программного обеспечения они хотят установить. 

# Некоторые недостатки Chocolatey

`Потенциальные риски безопасности.` Поскольку пакеты Chocolatey могут создавать любые пользователи, есть риск установки небезопасных пакетов. Рекомендуется использовать только надёжные источники. 

`Ограниченный графический интерфейс.` Chocolatey в основном работает через командную строку, что может быть неудобно для тех, кто предпочитает графические интерфейсы. 

`Стоимость коммерческих лицензий.` Хотя Chocolatey бесплатен для личного использования, для коммерческих целей и использования расширенных функций требуется платная лицензия.
 
`Проблемы с зависимостями.` Иногда в пакетах могут быть проблемы с зависимостями, которые необходимо решать вручную, что может усложнить простой процесс. 

`Сложность для новичков.` Для пользователей, не знакомых с инструментами командной строки или менеджерами пакетов, может быть сложно эффективно использовать Chocolatey.


