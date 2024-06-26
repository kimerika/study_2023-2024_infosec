---
## Front matter
title: "Лабораторная работа 5"
subtitle: "Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в кон- соли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.1."
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

Получение практических навыков работы в консоли с расширенными атрибутами файлов1

# Теоретическое введение

                                                                                |

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

# Выполнение лабораторной работы

1. От имени пользователя guest определили расширенные атрибуты файла /home/guest/dir1/file1 командой lsattr /home/guest/dir1/file1  (рис. [-@fig:001]).

![1](image/1.png){#fig:001 width=70%}

2. Установили командой chmod 600 file1 на файл file1 права, разрешающие чтение и запись для владельца файла (рис. [-@fig:002]).

![2](image/2.png){#fig:002 width=70%}

3. Попробовали установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest: chattr +a /home/guest/dir1/file1 (рис. [-@fig:003]).

![3](image/3.png){#fig:003 width=70%}

4. Зашли на третью консоль с правами администратора либо повысили права с помощью команды su. Попробовали установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперполь зователя: chattr +a /home/guest/dir1/file1 (рис. [-@fig:004]).

![4](image/4.png){#fig:004 width=70%}

5. От пользователя guest проверили правильность установления атрибута: lsattr /home/guest/dir1/file1 (рис. [-@fig:005]).

![5](image/5.png){#fig:005 width=70%}

6. Выполнили дозапись в файл file1 слова «test» командой echo "test" /home/guest/dir1/file1. После этого выполнили чтение файла file1 командой cat /home/guest/dir1/file1. Убедились, что слово test было успешно записано в file1.  (рис. [-@fig:006]).

![6](image/6.png){#fig:006 width=70%}

7. Попробовали удалить файл file1 либо стереть имеющуюся в нём информацию командой echo "abcd" > /home/guest/dirl/file1.Попробовали переименовать файл. (рис. [-@fig:007]).

![7](image/7.png){#fig:007 width=70%}

8. Попробовали с помощью команды chmod 000 file1 установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. Команда сработала. (рис. [-@fig:008]).

![8](image/8.png){#fig:008 width=70%}

9. Сняли расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя командой
chattr -a /home/guest/dir1/file1. (рис. [-@fig:009]).

![9](image/9.png){#fig:009 width=70%}

10. Повторили операции, которые ранее не удавалось выполнить. (рис. [-@fig:010]).

![10](image/10.png){#fig:010 width=70%}



# Выводы

В результате выполнения работы вы повысили свои навыки использования интерфейса командой строки (CLI), познакомились на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа. Имели возможность связать теорию дискреционного разделения доступа (дискреционная политика безопасности) с её реализацией на практике в ОС Linux. Составили наглядные таблицы, поясняющие какие операции возможны при тех или иных установленных правах.

# Список литературы{.unnumbered}

::: {#refs}
:::
