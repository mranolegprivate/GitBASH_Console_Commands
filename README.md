BASH-Console-Commands
Командные строки Linux.

Шпаргалка по bash
Шпаргалка основных команд Git Bash, терминала OSX, терминала linux.
Командная оболочка Bash является одним из нескольких главных компонентов в дистрибутивах Linux. Она позволяет читать и запускать команды, выполнять скрипты, работать с файлами. Наличие Bash не менее важно для полноценного функционирования операционных систем семейства Linux, чем ядро или рабочее окружение.

Суть
Консоль — удобный и быстрый инструмент управления компьютером. Вводим команду текстом, получаем результат или сообщение об ошибке с указанием в чём ошибка.

Работая с консолью, мы всегда «находимся» в какой-то папке (это указано в строке над курсором). Если там написано ~, то мы в папке пользователя (зависит от настроек Windows, чаще всего это C:/Users/ВАШЕИМЯПОЛЬЗОВАТЕЛЯ/), если там /d/projects, мы в папке D:/projects.

Открыть любой txt файл
vim file_1.json
Написать туда что-нибудь, текст.
{
        "year":         2022,
        "name":         "Andrei",
        "active":       True,
        "skills":       ["Python", "c++", "JS"]
}
Сохранить и выйти.
Esc
:qw
Выйти из папки на уровень выше
cd ../
Переместить любые 2 файла, которые вы создали в любую другую папку.
mv folder_1/file_1.json folder_1/file_1.txt folder_2
Скопировать любые 2 файла, которые вы создали в любую другую папку.
cp folder_1/file_2.json folder_1/file_2.txt folder_2
Найти файл по имени
find folder_1/file_3.txt
Просмотреть содержимое в реальном времени
tail -F file_1.json
Вывести несколько первых строк из текстового
файла

head -n3 file_1.json
{
	"year":		2022
	"name": 	"Andrei",
Вывести несколько последних строк из текстового файла
tail -n3 file_1.json
	"active": 	True,
	"skills":	["Python", "c++", "JS"]
}
Просмотреть содержимое длинного файла
(команда less) изучите как она работает.

less long_file.json
q
Вывести дату и время
date
Файловая система
Просмотр содержимого папки
pwd                     # выводит текущий путь (сокращение от PRINT WORK DIRECTORY)
ls                      # показать содержимое папки
ls -l                   # отображает расширенную информацию о файлах и папках
ls -a                   # то же, но показывать и скрытые файлы и папки
ls -a -1                # то же, но в один столбец
ls -hF -1 --sort=extension # показать содержимое папки «красиво, в один столбец»
ls build/css            # показать содержимое папки ТЕКУЩАЯ_ПАПКА/build/css
ls /d/projects          # показать содержимое папки D:/projects
Просмотр содержимых файлов cat и текстовые редакторы
cat {и имя файла}         # показать содержимое файла или файлов если через пробел написать файлы
cat text1.txt text2.txt  # просмотр строк в файлах вместе
less file.txt           # встроенная утилита для просмотра больших файлов типа Lorem Ipsum в отдельном окне
q                        # возврат обратно в bash
nano file.txt           # открытие файла в текстовом редакторе
vi имя файла            # текстовый редактор
esc для выхода из редактора обратно в консоль
Замена информации в файле
echo хелоу                 # выводит информацию на следующую строку в консоли
echo привет > file.txt           # заменяет текс в файле на "привет" в file.txt
echo пока >> file.txt  # две >> добавляет информацию типа "привет пока" 
вывод команды на ввод другой
grep   ищет информацию в файле

cat file.txt | grep i слово     # будет искать слово в файле file.txt (i ставится чтобы искал в любом регистре)  
Перемещение по файловой системе
Пользователь всегда находится в какой-то папке, она (или полный путь) всегда показана до области ввода команд.

cd projects             # переход в папку projects, которая есть текущей папке
cd /d/projects          # windows: переход в папку projects, расположенную по адресу D:/projects 
cd /c/Program\ Files    # windows: переход в C/:Program Files 
cd .                    # текущая директория
cd ..                   # переход к родительской папке 
cd ~                    # домашняя директория
cd -                    # переход к последней рабочей папке
Чтобы не набирать имя папки целиком, наберите первые пару символов и нажмите Tab — произойдет автодополнение (если нет двух папок, начинающихся с введенных символов, иначе будут показаны сами эти папки). Справедливо для любой команды.

Создание папок и файлов
mkdir project                        # создать папку с именем «project»
mkdir project project/css project/js # создать несколько папок
mkdir -p project/{css,js}            # то же, что выше
touch index.html                     # создать файл
touch index.html css/style.css js/script.js # создать файлы (папки css/ и js/ должны уже существовать)
Копирование файлов
cp index.html catalog.html # копирование файла index.html в тот же каталог с переименованием в catalog.html
cp index.html old/         # копирование файла index.html в папку old/ (все произойдет в текущей папке)
cp temp/ temp2/ -r         # дублирование каталога
Переименование или перемещение файлов
mv index.html old              # перемещение файла в папку
mv index.html old/new_name.txt # перемещение файла в папку с переименованием файла
mv order.txt orderNew.txt      # переименовать файл
Удаление папок и файлов
rm ghost.png             # удалить файл
rm -rf old               # удалить папку и всё из нее
Команды для процессов
ps         # команда которая отображает какие процессы идут в данной консоли
ps x       # для отображение всех процессов
ps u       # процессы только для нашего пользователя
ps au      # все процессы всех пользователей в терминале
ps aux     # вообще все
top        # таблица для просмотра всех процессов для просмотра, что нагружает нашу систему для выхода из системы q
kill и номер PID     # остановка процесса 
Команды для отправления запросов на терминал
ping google.com        #скорость реагирования между сервером и компьютера, в данном случае скорость между терминалом и гуглом
ping -c 3 google.com   # где 3 это количество пакетов которые мы отправили
ping -c 3 -i 3 google.com # где 3 это отправка пакетов каждые 3 секунды ( по умолчанию 1 сек)
Обращения к сайтам и получение ответов от них
curl -L ya.ru                #  для запроса яндекса пакетов
curl -L ya.ru --verboce     # дополнительная информация и сведения 
  curl -Х  и ets. также курл можно использовать в запросах через сайт reqres.in для запроса типа Get 
Алиасы
Для команд можно создавать алиасы (синонимы). Для этого в папке пользователя (OSX и linux) или в C:/Users/ИМЯ_ПОЛЬЗОВАТЕЛЯ/.bashrc (Windows) нужно вписать строки, наподобие alias pro='cd /d/projects' (одна строка в файле — один алиас)..

alias                 # отобразит алиасы, которые уже заданы в системе   
alias c='clear'       # создаст алиас который будет очищать консоль
unalias c             # удалит алиас " c "
unalias -a            # удалит все записанные алиасы
Разное
Подборка команд, показывающих бОльшую скорость работы с консолью, чем с GUI или просто удобных команд. Многие из них могут быть реализованы различными путями с GUI, что ничуть не умаляет удобства консоли.

clear                 # очистить консоль
df -h                 # показать статистику использования пространства на дисках
grep -i -n --color 'carousel' index.html css/style.css # найти слово carousel в двух указанных файлах (с игнором регистра), вывести строки с этим словом и номера строк (искомое слово подсветить)
grep word -r project  # найти слово word во всех файлах в папке project
find . -iname '*ind*' # найти в текущей папке (и подпапках) все файлы, имена которых содержат ind и показать списком
ls -a >> file.txt     # записать в file.txt результат вывода команды ls -a
ls src/less/mixins    # показать содержимое папки с указанным путем без перехода в неё
echo  "Some text"     # вывод текста в консоль 
chmod +x ./fileName   # сделать файл исполняемым 
whoami                # выводит имя пользователя 
Использование переменных
Переменные позволяют хранить в файле сценария информацию, например — результаты работы команд для использования их другими командами.

Существуют два типа переменных, которые можно использовать в bash-скриптах:

Переменные среды - переменные установленые в среде
echo $HOME
echo "Env variable $HOME"
Пользовательские переменные - хранят значение до тех пор, пока не завершится выполнение сценария.
#!/bin/zsh
grade=5 
person="Adam"
echo "$person is a good boy, he is in grade $grade"
Подстановка команд в переменные
Одна из самых полезных возможностей bash-скриптов — это возможность извлекать информацию из вывода команд и назначать её переменным, что позволяет использовать эту информацию где угодно в файле сценария.

Сделать это можно двумя способами.

С помощью значка обратного апострофа «`»
mydir=`pwd`
С помощью конструкции $()
mydir=$(pwd)
А скрипт, в итоге, может выглядеть так:

#!/bin/bash
mydir=$(pwd)
echo $mydir
В ходе его работы вывод команды pwdбудет сохранён в переменной mydir, содержимое которой, с помощью команды echo, попадёт в консоль.

Математические операции
Для выполнения математических операций в файле скрипта можно использовать конструкцию вида $((a+b))

#!/bin/bash
var1=$(( 5 + 5 ))
echo $var1
var2=$(( $var1 * 2 ))
echo $var2
Управляющая конструкция if-then
В некоторых сценариях требуется управлять потоком исполнения команд. Например, если некое значение больше пяти, нужно выполнить одно действие, в противном случае — другое. Подобное применимо в очень многих ситуациях, и здесь нам поможет управляющая конструкция if-then. В наиболее простом виде она выглядит так

if команда
then
команды
fi 
#!/bin/bash
if pwd
then
echo "It works" 
fi
Пример: надо найти некоего пользователя в /etc/passwd, и если найти его удалось, сообщить о том, что он существует.

#!/bin/bash
user=likegeeks
if grep $user /etc/passwd
then
echo "The user $user Exists"
fi
Управляющая конструкция if-then-else
Для того, чтобы программа смогла сообщить и о результатах успешного поиска, и о неудаче, воспользуемся конструкцией if-then-else. Вот как она устроена:

if команда
then
команды
else
команды
fi
Если первая команда возвратит ноль, что означает её успешное выполнение, условие окажется истинным и выполнение не пойдёт по ветке else. В противном случае, если будет возвращено что-то, отличающееся от нуля, что будет означать неудачу, или ложный результат, будут выполнены команды, расположенные после else.

#!/bin/bash
user=anotherUser
if grep $user /etc/passwd
then
echo "The user $user Exists"
else
echo "The user $user doesn’t exist"
fi
Конструкция CASE
Если вы столкнулись с парой различных возможных действий, то использование оператора case может быть более полезным, чем вложенные операторы if. Для более сложных условий используйте пример, как показано ниже

case "$extension" in
  "jpg"|"jpeg") echo "It's image with jpeg extension." ;;
  "png")        echo "It's image with png extension."  ;;
  "gif")        echo "Oh, it's a giphy!"               ;;
  *)            echo "Woops! It's not image!"          ;;
esac
Циклы
В Bash есть четыре типа циклов: for, while, until и select.

FOR
# 1
for arg in elem1 elem2 ... elemN
do
  # statements
done
# 2
for i in {1..5}; do echo $i; done
# 3
for (( i = 0; i < 10; i++ )); do
  echo $i
done
# 4
for FILE in $HOME/*.bash; do
  mv "$FILE" "${HOME}/scripts"
  chmod +x "${HOME}/scripts/${FILE}"
done
WHILE - Цикл while проверяет условие и перебирает последовательность команд, пока это условие истинно. Условие - это не что иное, как первичное значение, используемое в условиях if..then.
while [[ condition ]]
do
  # statements
done
# Squares of numbers from 0 through 9
x=0
while [[ $x -lt 10 ]]; do # value of x is less than 10
  echo $(( x * x ))
  x=$(( x + 1 )) # increase x
done
UNTIL - Цикл until - полная противоположность цикла while. Какое-то время он проверяет условие теста, но продолжает цикл, пока это условие ложно
until [[ condition ]]; do
  #statements
done
SELECT - Цикл выбора помогает нам организовать пользовательское меню. Он имеет почти тот же синтаксис, что и цикл for
select answer in elem1 elem2 ... elemN
do
  # statements
done
В этом примере пользователю задается вопрос, какой диспетчер пакетов он хотел бы использовать. Затем он спросит, какой пакет мы хотим установить, и, наконец, приступит к его установке.

PS3="Choose the package manager: "
select ITEM in bower npm gem pip
do
  echo -n "Enter the package name: " && read PACKAGE
  case $ITEM in
    bower) bower install $PACKAGE ;;
    npm)   npm   install $PACKAGE ;;
    gem)   gem   install $PACKAGE ;;
    pip)   pip   install $PACKAGE ;;
  esac
  break # avoid infinite loop
done
LOOP CONTROL - Бывают ситуации, когда нам нужно остановить цикл до его нормального завершения или перешагнуть через итерацию. В этих случаях мы можем использовать встроенные в оболочку операторы break и continue.
Оператор break используется для выхода из текущего цикла до его завершения Оператор continue проходит одну итерацию

for (( i = 0; i < 10; i++ )); do
  if [[ $(( i % 2 )) -eq 0 ]]; then continue; fi
  echo $i
done
Сравнение чисел
В скриптах можно сравнивать числовые значения. Ниже приведён список соответствующих команд.

Сравнения пишем в [ ] обязательно пробелы в скобках

# eq - equal  
# ge - greater equal   
# gt - greater than     
# le - less equal  
# lt - less than  
# ne - not equal  
n1 -eq n2 # Возвращает истинное значение, если n1 равно n2.
n1 -ge n2 # Возвращает истинное значение, если n1 больше или равно n2.
n1 -gt n2 # Возвращает истинное значение, если n1 больше n2.
n1 -le n2 # Возвращает истинное значение, если n1 меньше или равно n2.
n1 -lt n2 # Возвращает истинное значение, если n1 меньше n2.
n1 -ne n2 # Возвращает истинное значение, если n1 не равно n2.
val1=6
if [ $val1 -gt 5 ]
then
echo "The test value $val1 is greater than 5"
else
echo "The test value $val1 is not greater than 5"
fi
Сравнение строк
В сценариях можно сравнивать и строковые значения.
Операторы сравнения выглядят довольно просто, однако у операций сравнения строк есть определённые особенности, которых мы коснёмся ниже. Вот список операторов.

str1 = str2   # Проверяет строки на равенство, возвращает истину, если строки идентичны.
str1 != str2  # Возвращает истину, если строки не идентичны.
# операторы «>» и «<» необходимо экранировать с помощью обратной косой черты,
str1 \< str2   # Возвращает истину, если str1 меньше, чем str2.
str1 \> str2   # Возвращает истину, если str1 больше, чем str2.
-n str1       # Возвращает истину, если длина str1 больше нуля.
-z str1       # Возвращает истину, если длина str1 равна нулю.  
#!/bin/bash
user ="likegeeks"
if [ $user = $USER ]
then
echo "The user $user  is the current logged in user"
fi
Проверки файлов
Kоманды позволяют проверять различные условия, касающиеся файлов

-d file         # Проверяет, существует ли файл, и является ли он директорией.
-e file         # Проверяет, существует ли файл.
-f file         # Проверяет, существует ли файл, и является ли он файлом.
-r file         # Проверяет, существует ли файл, и доступен ли он для чтения.
-s file         # Проверяет, существует ли файл, и не является ли он пустым.
-w file         # Проверяет, существует ли файл, и доступен ли он для записи.
-x file         # Проверяет, существует ли файл, и является ли он исполняемым.
file1 -nt file2 # Проверяет, новее ли file1, чем file2.
file1 -ot file2 # Проверяет, старше ли file1, чем file2.
-O file         # Проверяет, существует ли файл, и является ли его владельцем текущий пользователь.
-G file         # Проверяет, существует ли файл, и соответствует ли его идентификатор группы идентификатору группы текущего пользователя.
#!/bin/bash
mydir=/home/likegeeks
if [ -d $mydir ]                    # если файл сущетсвует и он является директорией
then
echo "The $mydir directory exists"  # выводим сообщение
cd $mydir                          # переходим в него 
ls                                  # отображаем содержимое
else                                # ИНАЧЕ
echo "The $mydir directory does not exist"
fi
Операторы
Пайпы | - передает результат выполненной инструкции следующему пайпу

# command1 | command2 | command3  
ls -l | grep .md$ | less
Точка с запятой ; - выполняет команды последовательно

# command2 will be executed after command1
command1 ; command2
Амперсанд & - оболочка выполняет команду асинхронно в подоболочке. Другими словами, эта команда будет выполняться в фоновом режиме

Двойной амперсанд (И) && - вторая команды будет выполнена только в случае УСПЕШНОГО заверения первой команды

# command2 will be executed if, and only if, command1 finishes successfully (returns 0 exit status)
command1 && command2
Двойной пайп (ИЛИ) - вторая команды будет выполнена только в случае НЕУДАЧНОГО заверения первой команды

# command2 will be executed if, and only if, command1 finishes unsuccessfully (returns code of error)
command1 || command2
Тестовые [ ] - Эти выражения помогают нам указать результаты условного выражения. Используются обычно в блоках if

# Single-line
if [[ 1 -eq 1 ]]; then echo "true"; fi
# Multi-line
if [[ 1 -eq 1 ]]; then
  echo "true"
fi
# Single-line
if [[ 2 -ne 1 ]]; then echo "true"; else echo "false"; fi
# Multi-line
if [[ 2 -ne 1 ]]; then
  echo "true"
else
  echo "false"
fi
