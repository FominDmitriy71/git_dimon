# Работа с GIT
## 1. Проверка наличия установленного GIT
В терминале выполнить команду `git --version` Если Git установлен, появится сообщение о версии программы, иначе будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git c сайта https://git-scm.com/downloads Устанавливаем с настройками по умолчанию.

## 3. Настройка GIT
При первом использовании GIT необходимо представиться. Для этого нужно ввестив терминале 2 команды:
```
Bash
git config --global user.name "Ваше имя английскими буквами"
git config --global user.email "Ваша почта"
```
## 4. Инициализация репозитория.
Для работы с файлами необходимо создать папку и файл и  выбрать ее в VS.
Инициализация локального репозитория производится командой ``git init``

 ## 5. Сохранение файла и просмотр состояния GIT
 Сохранение файла производится комбинацией клавиш ctrl+S.
 После сохранения команда ``git status``
 покажет, что файл модифицирован.

 Пример просмотра статуса 
 
 ```
  $ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)   
  (use "git restore <file>..." to discard changes in working directory)
        modified:   insruction.md
 ```
 ``git status`` - показывает текущее состояние файов в репозитории, с помощью команды можно посмотреть готов ли файл для добавления коммита.

## 6. Создание коммитов
1. Необходимо после фиксации состояния ``ctrl+S`` добавить состояния для сохранения коммита
2. Командой `git add "Имя файла"` - добавление файла для коммита
3. команда ``git commit -m`` производится добавление коммита и создается хеш код для последующего возможного восстановления.
4. Командой ``git commit -am`` возможно одновременно добавить файл к коммиту и произвести коммит одновременно.

Пример успешного добавления коммита 
```
$ git commit -a -m "Создание коммитов"
[master 700b3ad] Создание коммитов
 1 file changed, 7 insertions(+)
```

## 7. Просмотр версий коммитов
Командой `git log` можно просматривать зафиксированные коммиты.
Командой `git checkout` 
происходит переход между сохраненными версиями
`git checkout master` - загрузка самой последней версии в дереве master

Примет просмотра хеша с коммитами
```
$ git log
commit 700b3ad795c0f48f6031970a7f86a51e55b223e7 (HEAD -> master)
Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
Date:   Wed Sep 6 22:55:55 2023 +0300

    Создание коммитов

commit d9dc57cb538909cbb80866941ce18f9c8dcd092a
Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
Date:   Wed Sep 6 22:49:56 2023 +0300

    Добавление информации об инициализации и сохранении        

commit f05e571883a495f65c1eb88098a8020b865b856b
Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
Date:   Wed Sep 6 19:28:33 2023 +0300
```
`git switch` - переход между версиями коммитов

## 8. Просмотр изменений 
``git diff`` - команда,  которая показывает разницу между текущем состоянием и сохраненным коммитом

```
$ git diff
diff --git a/insruction.md b/insruction.md
index e6ecf6d..ad44409 100644
--- a/insruction.md
+++ b/insruction.md
@@ -73,3 +73,5 @@ Date:   Wed Sep 6 19:28:33 2023 +0300        
 ```
 `git switch` - переход между версиями коммитов

+## 8. Просмотр изменений 
+``git diff`` - команда,  которая показывает разницу между     
\ No newline at end of file


## 9. Игнорирование файлов

Для того, чтобы исключить из отслеживания в репозитории определенные файлы или папки необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответствующие таким файлам или папкам.

## 10. Создание веток в Git
По умолчанию имя основной ветки в Git -
`master`.
Создать ветку можно командой:
```Bash
git branch <Имя новой ветки >
```
Список веток в репозитории можно посмотреть с помощью команды `git branch`

Пример:
```Bash
$ git branch 
* master
  test
  test2
  test3
  test4
```

`git checkout` "Имя ветки"- команда выбора нужной ветки
`git switch` "Имя ветки"- команда для перехода между созданными ветками


## 11. Слияние веток и разрешение конфликтов

Для слияния выбранной ветки с текущей нужно выполнить команду 
```Bash

git merge <Название выбранной ветки >
```
Если была изменена одна и таже часть файла в обеих ветках,   может возникнуть конфликт
Конфликт может быть разрешен посредством терминала или графического интерфейса.
<<<<<<< HEAD

Пример:
```Bash
=======
>>>>>>> test2

<<<<<<< HEAD
=======
Пример:
```Bash

>>>>>>> test3
## 12. Тест

Исправленный текст

<<<<<<< HEAD
=======
<<<<<<< HEAD
3. тест тест
=======
>>>>>>> test2
```


## 12. Удаление веток
Для удаления веток можно спользовать как полную так и сокращенную команду `delete`
Варианты написания: git branch ``--delete``, ``-d``, ``-D``
При написании заклавных букв команда git branch ``-D``, команда будет исполнятся принудительно
Пример:
```Bash
$ git branch --delete resolveConfkikts
Deleted branch resolveConfkikts (was 9fa91a5).

```

## 13. Визуализация лог коммитов

`git log --graph` - отображение дерева веток, где будут отображаться как создание новых веток, так и их слияние 

Пример:

```Bash
$ git log --graph
*   commit f86a16fb4a808941ece1b4778a1eccfb481a22de (HEAD -> master)
|\  Merge: 215c3ca 9f01de9
| | Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
| | Date:   Fri Sep 8 20:08:52 2023 +0300
| |
| |     Merge branch 'newvetka'
| |
| * commit 9f01de99d541d39226283d170756e6abc98c85ab
| | Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
| | Date:   Fri Sep 8 20:07:39 2023 +0300
| |
| |     Тест
| |
* | commit 215c3ca24a5c54e21b3cb045c7f9c077f8bd661a
|/  Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
|   Date:   Fri Sep 8 20:01:22 2023 +0300

Пример №2


 commit 15aa0fe6f8edf74c21183d620e8f43c06e217fd6
|\  Merge: 9fa91a5 15f1e47
| | Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
| | Date:   Fri Sep 8 16:25:13 2023 +0300
| |
| |     Merge branch 'createBranches'
| |
| * commit 15f1e4799ab7df68231b18bd083af224a3153947
| | Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
| | Date:   Fri Sep 8 16:18:40 2023 +0300
| |
| |     Зафиксировали 11 пункт, разрешили противоречия
| |
| * commit 799f5014bba90e49c66a59593469c6aa85a3e8b3
| | Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
| | Date:   Fri Sep 8 00:54:59 2023 +0300
| |
| |     Добавили раздел 10 - Создание веток в GIT и команду git branch
| |
* | commit 9fa91a5f5de308f954cb044a4f7793acaef6d7bb
| | Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
| | Date:   Fri Sep 8 15:35:23 2023 +0300
| |
| |     Добавили  11 пункт о слиянии веток
| |
* | commit 36fdb686400f2c07403819024f8b5dbfc134ebc5
|/  Author: Dmitriy Fomin <dmitriytulskiy@gmail.com>
|   Date:   Fri Sep 8 15:22:04 2023 +0300

```

## 14. Тестовый раздел

Пример тестового текста
<<<<<<< HEAD

4. тест, тест
=======
1. тест тест

<<<<<<< HEAD
## 12. Тест

2. Тест, Тест
=======
>>>>>>> test4
>>>>>>> test3
>>>>>>> test2
