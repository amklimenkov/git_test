# Создание локального репозитория

1. Узнаем имя директории в которой находимся и просмотрим её содержимое
    ```Bash
    amk@pop-os:~$ pwd
    /home/amk
    amk@pop-os:~$ ls -a
     ..              .gradle            .var
     Arduino         .ipython           .viminfo
     ............................................................
    ```
2. Создаем рабочую директорию и переходим в неё
     ```Bas
    amk@pop-os:~$ mkdir lab_opi_01
    amk@pop-os:~$ l
     Arduino/         PycharmProjects/   Загрузки/         *lab_opi_01/ 
    ..................................................................
    amk@pop-os:~$ cd lab_opi_01/
    amk@pop-os:~/lab_opi_01$ pwd
    /home/amk/lab_opi_01
    ```
3. Инициализируем репозиторий и убеждаемся в успешности инициализации
    ```Bash
    mk@pop-os:~/lab_opi_01$ git init
    Инициализирован пустой репозиторий Git в /home/amk/lab_opi_01/.git/
    amk@pop-os:~/lab_opi_01$ ls -a
    .  ..  .git
    ```

# Подготовка в работе
1. Проверяем корректности _имени пользователя_ и _адреса электронной почты_
    ```
    amk@pop-os:~/lab_opi_01$ git config --list
    user.name=kam23u910
    user.mail=kam23u910@student.bmstu.ru
    credential.helper=cache
    core.repositoryformatversion=0
    core.filemode=true
    core.bare=false
    core.logallrefupdates=true
    amk@pop-os:~/lab_opi_01$
    ```
    > Так как команда ```git config --list``` выдаёт уде корректные данные, то мы не булем их менять с помощью команд ```git config user.name ``` и ```git config user.mail```
    
2. Скопируем исходные файлы задание с расширением *.py в директорию лабораторной работы и убедимся в успешности операции
	```Bash
   	amk@pop-os:~/lab_opi_01$ cp ~/Загрузки/src_2/*.py ~/lab_opi_01/ 
   	amk@pop-os:~/lab_opi_01$ ls -a
    .  ..  .git  iarray.py  main.py
    ```
3. Попробуем запустить файл main.py в директории нашей лабораторной
	```Bash
    amk@pop-os:~/lab_opi_01$ python3 main.py
    0 5 3 8 
    Max pos = 3
    amk@pop-os:~/lab_opi_01$ ls
    iarray.py  main.py  __pycache__
    ```
	> В рабочей директории появилась папка __pycache__, которая не должна отслеживаться системой контроля версий. Поэтому добавим её в файл .gitignore
4. Добавляем .gitignore файл в директорию
	```Bash
    amk@pop-os:~/lab_opi_01$ cat > .gitignore
	**/__pycache__/**	
    amk@pop-os:~/lab_opi_01$ cat .gitignore 
	**/__pycache__/**
	```
5. Посмотрим файлы, находящиеся под версионным контролем
	```Bash
    amk@pop-os:~/lab_opi_01$ git status 
    Текущая ветка: master

    Еще нет коммитов

    Неотслеживаемые файлы:
      (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
        .gitignore
        iarray.py
        main.py

    индекс пуст, но есть неотслеживаемые файлы
    (используйте «git add», чтобы проиндексировать их)
    ```
	> Ни один файл не находится под версионным контролем
6. Добавим файл .gitignore под версионный контроль
	```Bash
    amk@pop-os:~/lab_opi_01$ git add .gitignore
    amk@pop-os:~/lab_opi_01$ git status
    Текущая ветка: master

    Еще нет коммитов

    Изменения, которые будут включены в коммит:
      (используйте «git rm --cached <файл>...», чтобы убрать из индекса)
        новый файл:    .gitignore

    Неотслеживаемые файлы:
      (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
        iarray.py
        main.py
    ```
7. Сделаем commit (зафиксируем изменения файла .gitignore)
	```Bash
    amk@pop-os:~/lab_opi_01$ git commit -m ".gitignore was added"
    amk@pop-os:~/lab_opi_01$ git log
    commit e4477a0296859a5c2933fdc69865851dd0a639de (HEAD -> master)
    Author: Klimenkov Artem <kam23u910@student.bmstu.ru>
    Date:   Fri Feb 16 19:12:02 2024 +0300

        .gitignore was added
    ```
8. Добавим под версионный контроль саму программу 
	```Bash
    amk@pop-os:~/lab_opi_01$ git add iarray.py main.py
    amk@pop-os:~/lab_opi_01$ git status 
    Текущая ветка: master
    Изменения, которые будут включены в коммит:
      (используйте «git restore --staged <файл>...», чтобы убрать из индекса)
        новый файл:    iarray.py
        новый файл:    main.py
	```
9. Зафиксируем изменения
	```Bash
    
    amk@pop-os:~/lab_opi_01$ git commit -m "Initial version of python program was added"
    [master ed9441c] Initial version of python program was added
     2 files changed, 45 insertions(+)
     create mode 100644 iarray.py
     create mode 100644 main.py
	amk@pop-os:~/lab_opi_01$ git log
    commit ed9441c2a62e68c8c7557c73d400e306cf6e6eb7 (HEAD -> master)
    Author: Klimenkov Artem <kam23u910@student.bmstu.ru>
    Date:   Fri Feb 16 19:17:22 2024 +0300

        Initial version of python program was added

    commit e4477a0296859a5c2933fdc69865851dd0a639de
    Author: Klimenkov Artem <kam23u910@student.bmstu.ru>
    Date:   Fri Feb 16 19:12:02 2024 +0300

        .gitignore was added
    ```

# Выполнение лабораторной работы
1. Посмотрим исходный код программы
	```Bash
    amk@pop-os:~/lab_opi_01$ cat main.py 
    from iarray import *

    def test_1():
      arr = list()

      arr.append(0)
      arr.append(5)
      arr.append(3)
      arr.append(8)

      return arr, 4


    def main():
      arr, n = test_1()

      print_array(arr, n)

      print("Max pos = " + str(get_max_pos(arr, n)))


    if __name__ == '__main__':
      main()
    amk@pop-os:~/lab_opi_01$ cat iarray.py 
    def get_max_pos(arr, n):
      max = arr[0];

      i = 1
      while (i < n):
        if (arr[i] > max):
          max = arr[i]
          j = i

        i += 1

      return j


    def print_array(arr, n):
      i = 0
      while (i < n):
        print(arr[i], end = " ")
        i += 1

      print("")
2. Назначение программы

   >Программа предназначена для нахождения в списке индекса максимального элемента этого списка.

   |Наименование функции|Назначение функции|
   |--------------------|------------------|
   |print_array(arr,n)|Принимает на вход список и число __n__, печатает первые __n__ элементов списка|
   |get_max_pos(arr,n)|Принимает на вход список и __n__, возвращает индекс максимального элемента из первых __n__ элементов|
   |main()|Вызывает функцию тестов, функцию печати тестового массива и выводит на экран позицию максимального элемента при текущих тестовых значениях списка и __n__|
   |test_1()|Функцию задаёт тестовый список, возвращает тестовый список и число __n__ необходимое для работы функции _get_max_pos(arr,n)_
3. Добавление нового теста, выявляющего ошибку
	* Открываем редактор nano
	* Добавляем код функции _test_2()_ 
	* Добавляем код вызова функции _test_2()_ в функцию _main()_
	* Форматируем вывод функции _main()_
4. Анализ изменений
	```Bash
    amk@pop-os:~/lab_opi_01$ git status
    Текущая ветка: master
    Изменения, которые не в индексе для коммита:
      (используйте «git add <файл>...», чтобы добавить файл в индекс)
      (используйте «git restore <файл>...», чтобы отменить изменения в рабочем каталоге)
        изменено:      main.py

    индекс пуст (используйте «git add» и/или «git commit -a»)
    amk@pop-os:~/lab_opi_01$ git diff
    diff --git a/main.py b/main.py
    index 2c8aaa2..64b53ea 100644
    --- a/main.py
    +++ b/main.py
    @@ -10,14 +10,28 @@ def test_1():

       return arr, 4

    +def test_2():^M
    +  arr_test = []^M
    +  ^M
    +  arr_test.append(100)^M
    +  arr_test.append(20)^M
    +  arr_test.append(45)^M
    +  arr_test.append(36)^M
    +  arr_test.append(55)^M

    -def main():
    -  arr, n = test_1()
    +  return arr_test, 5^M

    -  print_array(arr, n)
    +def main():^M
    +  arr_1, n_1 = test_1()^M
    +  arr_2, n_2 = test_2()^M

    -  print("Max pos = " + str(get_max_pos(arr, n)))
    -
    +  print("Test 1")^M
    +  print_array(arr_1, n_1)^M
    +  print("Max pos = " + str(get_max_pos(arr_1, n_1)))^M
    +  ^M
    +  print("Test 2")^M
    +  print_array(arr_2, n_2)^M
    +  print(f"Max pos = {get_max_pos(arr_2, n_2)}")^M
	```
    > Команда ```git status``` показывает, что есть изменения в файле main.py, но они не проиндексированы, значит изменения не попадут в следующий коммит. Применим позже команду ```git add main.py``` и затем сделаем коммит.
    > Команда git diff показывает изменения файла с последнего коммита. В строке ```diff --git a/main.py b/main.py ``` отображаются входные данные сравнения (т.е для сравнения переданы файлы ```a/main.py``` и ```b/main.py```
# Самостоятельное изучение markdown 
1. Как добавлять картинки?
    ![](https://gas-kvas.com/uploads/posts/2023-01/1674334200_gas-kvas-com-p-kompyuternaya-grafika-risunki-3d-12.jpg)
    > Вставка картинки происходит двумя возможными способами 
    1. Вставка по ссылке 
    2. Вставка по относительному пути
    Вставка осуществляется конструкциейОписание картинки](Ccылка или относительный путь "Подпись под картинкой")
2. Пока пропустил
3. Как добавить ссылки для перехода между страницами wiki?
    >Добавление ссылки на wiki страницу осуществляется посредством конструкции```[Link Text](WikiPage)```, где _Link Text_ - отображаемое имя, при нажатии на которое происходит переход на нужную wiki страницу, имя которой задано с помощью _WikiPage_
4. Как писать комментарии?

    [это мой оставленный комментарий]: #
    
    > Комментарии составляются кострукцией ```[Comment here]: #```. **Обязательно делать строку отступа сверзу от комментария и снизу в коде. Иначе комментарий будет воприниматься как код.**
    
