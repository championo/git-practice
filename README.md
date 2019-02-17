# Git-practice (Episode #5)

**Git-practice** - проект посвященный получению практических навыков по работе с системой контроля версий (СКВ) Git.

## Что используется
* [Git](https://git-scm.com/)

## Что делаю

### Шаг 1

* **Создание нового репозитория на сайте [GitHub](https://github.com)**

Создаем через веб-интерфейс сайта репозиторий git-practice. При создании отказываемся от автоматического добавления файлов README.md, LICENCE.md, .gitignore.

Возможно создание репозитория через консоль. Для этого используйте, например,

* [hub](https://github.com/github/hub)
```bash
$ hub create
```
* [cURL](http://www.confusedbycode.com/curl)
```bash
curl -u 'userName' https://api.github.com/user/repos -d '{"name":"projectName","description":"Project description"}'
```

* **Создание локального репозитория**

```bash
cd git-practice
$ git init
```
Выполнение команд приведет к созданию в текущей папке скрытой директории .git. Git-директория - место, где СКВ хранит фиксации, указатели на ветви и т.п. 

Содержимое папки .git:

| Папка     | Описание                                                                  |
|-----------|---------------------------------------------------------------------------|
| hooks/    | Cкрипты (хуки/перехватчики), которые вызываются при выполнении git-задач  |
| info/     |                                                                           |
| objects/  | Объекты (commit, tree, blob и т.п.)                                       |
| refs/     | Указатели на ветки                                                        |

| Файлы         | Описание                      |
|---------------|-------------------------------|
| config        | Персональные настройки        |
| description   | Описание проекта              |
| HEAD          | Указатель на активную ветку   |

* **Создание удаленного репозитория на GitHub**

```bash
$ git remote add gp https://github.com/championo/git-practice.git
```
**Примечание.**

Используйте команду `git remote` для вывода списка репозиториев.

Команда `git remote add` используется с параметрами `git remote add [shortName] https://github.com/[userName]/[longName].git`, т.о. к репозиторию из консоли можно обращаться по короткому имени (псевдониму).

* **Создание файла, первая фиксация изменений и их отправка на сервер**

Создаем в папке git-practice (рабочая директория) файл README.md (в нем будем описывать проделанную работу). На данном этапе он не отслеживается СКВ.
Проверим статус:
```bash
$ git status
```
Git сообщает *"Untracked files: README.md"*. Добавим файл README.md в область подготовленных изменений (staging area):
```bash
$ git add README.md
```
**Примечание.** В область подготовленных изменений добавляем только те файлы, изменения в которых хотим зафиксировать и в дальнейшем отправить на сервер.

Проверка статуса сообщит нам *"Changes to be committed: new file README.md"*.

Делаем первую фиксацию изменений
```bash
$ git commit -m "First commit"
```
Отправляем данные из локального репозитория на удаленный репозиторий GitHub
```bash
$ git push -u gp master
```

### Шаг 2

* **Создание файла LICENSE.md, фиксация изменений и отправка на сервер**

Создаем в папке git-practice файл LICENSE.md. И напишем туда все что думаем о лицензии.
```bash
$ git add LICENSE.md
$ git add README.md
$ git commit -m "Add License file"
$ git push -u gp master
```

Далее некоторые команды будут опускаться, т.к. они уже освоены.

* **Создание ветки develop и файла .gitignore**

Создание ветки develop, являющейся ответвлением от ветки master
```bash
$ git checkout -b develop
```
После добавления файла .gitignore, отправляем данные на сервер
```bash
$ git commit -m "Add develop branch"
$ git push -u gp develop
```

* **Создание папки scripts в ветке develop, изменение .gitignore**

* **Слияние веток master и develop**
Внесем изменения в файл README.md в ветке develop. Отправим изменения на сервер и сольем ветки
```bash
$ git checkout master
$ git merge develop
```

* **Создание ветки jsbootstrap от develop, слияние с ней, удаление**

Здесь могла бы быть ваша реклама