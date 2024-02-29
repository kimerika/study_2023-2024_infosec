---
## Front matter
title: "Лабораторная работа 2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
author: "Ким Эрика Алексеевна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
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
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
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
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux1.


# Теоретическое введение

                                                                                |

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

# Выполнение лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы операционной системе создали учётную запись пользователя guest (использую учётную запись администратора):useradd guest. Задали пароль для пользователя guest (использую учётную запись администратора):passwd guest. Войдите в систему от имени пользователя guest.  (рис. [-@fig:001]).

![1](image/1.png){#fig:001 width=70%}

2. Определили директорию, в которой мы находимся, командой pwd. Сравнили её с приглашением командной строки. Определили, является ли она нашей домашней директорией? Если нет, зашли в домашнюю директорию. (рис. [-@fig:002]).

![2](image/2.png){#fig:002 width=70%}

3. Уточнили имя вашего пользователя командой whoami. (рис. [-@fig:003]).

![3](image/3.png){#fig:003 width=70%}

4. Уточнили имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. запомнили. Сравнили вывод id с выводом команды groups. (рис. [-@fig:004]).

![4](image/4.png){#fig:004 width=70%}

5. Просмотрите файл /etc/passwd командой cat /etc/passwd (рис. [-@fig:005]).

![5](image/5.png){#fig:005 width=70%}

6. Нашли в нём свою учётную запись.  (рис. [-@fig:006]).

![6](image/6.png){#fig:006 width=70%}

7. Замечание: в случае, когда вывод команды не умещается на одном экране монитора, используйте прокрутку вверх–вниз (удерживая клавишу shift, нажимайте page up и page down) либо программу grep в качестве фильтра для вывода только строк, содержащих определённые буквенные сочетания: cat /etc/passwd | grep guest (рис. [-@fig:007]).

![7](image/7.png){#fig:007 width=70%}

8. Определили существующие в системе директории командой ls -l /home/ (рис. [-@fig:008]).

![8](image/8.png){#fig:008 width=70%}

9. Проверили, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home (рис. [-@fig:009]).

![9](image/9.png){#fig:009 width=70%}

10. Создали в домашней директории поддиректорию dir1 командой mkdir dir1 (рис. [-@fig:010]).

![10](image/10.png){#fig:010 width=70%}

11. Определили командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1. (рис. [-@fig:011]).

![11](image/11.png){#fig:011 width=70%}

12. Сняли с директории dir1 все атрибуты командой chmod 000 dir1 и проверили с её помощью правильность выполнения команды ls -l (рис. [-@fig:012]).

![12](image/12.png){#fig:012 width=70%}

13.  Попытайтесь создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1 Объясните, почему вы получили отказ в выполнении операции по созданию файла? Оцените, как сообщение об ошибке отразилось на создании файла? Проверьте командой ls -l /home/guest/dir1 действительно ли файл file1 не находится внутри директории dir1. (рис. [-@fig:013]).

![13](image/13.png){#fig:013 width=70%}

14. Заполнили таблицу 2.1 (рис. [-@fig:014]), (рис. [-@fig:015]), (рис. [-@fig:016]).

![14](image/14.png){#fig:014 width=70%}

![15](image/15.png){#fig:015 width=70%}

![16](image/16.png){#fig:016 width=70%}

15. Заполнили таблицу 2.2 (рис. [-@fig:017]).

![17](image/17.png){#fig:017 width=70%}

# Выводы

Получили практических навыки работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux1.

# Список литературы{.unnumbered}

::: {#refs}
:::
