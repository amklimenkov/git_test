## Создание локального репозитория
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

## Подготовка в работе
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
    
2. Скопируем исходные файлы задание с расщирением *.py в репозиторий



## Самостоятельное изучение markdown 
1. Как добавлять картинки?
    ![Пример Картинки](https://gas-kvas.com/uploads/posts/2023-01/1674334200_gas-kvas-com-p-kompyuternaya-grafika-risunki-3d-12.jpg "hello")
