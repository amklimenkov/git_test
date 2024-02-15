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
     ```Bash
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
