# LR6
Лабораторная работа №6

---

## 1 Цель работы

Изучение базовых возможностей системы управления версиями. Получение опыта работы с Git Api, локальным и удаленным репозиторием.

## 2 Задание

1. Создать аккаунт на сайте GitHub.
2. Сделать копию в личное хранилище из
https://github.com/Kurtyanik/LR6/ (Fork).
3. Установить Git (https://git-scm.com/).
4. После установки настроить клиент git, введя имя пользователя (Группа Фамилия И.О.) и email.
5. Клонировать свой личный удалённый репозиторий на компьютер.
6. Добавить файл через интерфейс GitHub. Подтянуть изменения в локальный репозиторий. Работу продолжать локально.
7. Получить историю операций для каждой из веток.
8. Просмотреть последние изменения.
9. Выполнить слияние в ветку master, разрешив конфликт (можно использовать специальные редакторы или графический интерфейс git).
10. Удалить побочную ветку после успешного слияния.
11. Сделать изменения и зафиксировать их, оставляя комментарии, несколько раз.
12. Сделать откат коммита.
13. Создать ветку для отчёта.
14. Начать оформлять отчёт в файле README.md (разрешены сторонние редакторы с подсветкой синтаксиса), используя markdown синтаксис (https://guides.github.com/features/mastering-markdown/):
- В отчёте должен быть снимки экрана консоли и сторонних программ. Файлы снимков экрана разместить в отдельной папке.
- Лог команд (без результатов их выполнения).
При написании отчёта периодически делать коммиты, не забывать комментировать.
15. Получить историю операций в форматированном виде (сокращённый хэш + дата + имя автора + комментарий). Добавить её в отчёт и сделать финальную фиксацию изменений.

## 3 Ход работы

### Действия на сайте

#### 3.1 Создать аккаунт.
Поскольку аккаунт уже был создан (или создавался в первом семестре), остаётся использовать его. Процесс регистрации абсолютно стандартен для регистрации.

![](photo_dir/report_lab_6_1.png?raw=true)
<center><small>Рисунок 1</small></center>

#### 3.2 Сделать копию в личное хранилище.
Копия была выполнена с [репозитория преподавателя](https://github.com/Kurtyanik/LR6/).
Для создания копии на сайте GitHub используется функция Fork.

![](photo_dir/report_lab_6_4.png?raw=true)

После её выполнения будет получен собственный репозиторий, название можно задать самостоятельно.

![](photo_dir/report_lab_6_5.png?raw=true)

#### 3.3 Установить Git
Выполняется стандартным методом Next-Next-Install. Установлен с первого семестра.

#### 3.4 Настройка клиента Git
По аналогии с пунктами 1 и 3 уже было выполнено. При помощи команд можно проверить установленные настройки имени и почты.
```
git config --global user.name // Позволяет увидеть имя пользователя
git config --global user.email // Позволяет получить заданную почту
```

Задать новые значения можно так же, как и установить новые, командами `git config --global user.name <имя>` и ` git config --global user.email <почта>`

![](photo_dir/report_lab_6_3.png?raw=true)

#### 3.5 Клонирование репозитория на компьютер
Для клонирования была создана отдельная папка на диске F, а в неё был клонирован командой `git clone` репозиторий.

![](photo_dir/report_lab_6_6.png?raw=true)
![](photo_dir/report_lab_6_7.png?raw=true)
![](photo_dir/report_lab_6_8.png?raw=true)

#### 3.6 Добавление файла через интерфейс GitHub, подтягивание изменений на локальный репозиторий

В репозитории на GitHub при помощи кнопки Add file был добавлен файл my_tasks.md

![](photo_dir/report_lab_6_9.png?raw=true)
![](photo_dir/report_lab_6_10.png?raw=true)

Затем для подтягивания изменений была использована команда `git pull`, при помощи которой изменения с master Были добавлены на локальный компьютер.

![](photo_dir/report_lab_6_11.png?raw=true)

### Локальная работа

#### 3.7 Получение истории операций для каждой из веток

Для получения истории каждой из веток достаточно переключиться на неё при помощи команды `git checkout <название ветки>`, а затем ввести команду `git log`. Команда выведет историю последних коммитов в выбранной ветви, включая родительскую ветку.

![](photo_dir/report_lab_6_12.png?raw=true)

#### 3.8 Просмотр последних изменений

Для просмотра изменений используется команда `git status`. Она выводит в консоль статус ветки, список изменённых файлов.

![](photo_dir/report_lab_6_14.png?raw=true)

#### 3.9 Выполнение слияния с разрешением конфликта

Процесс слияния выполняется для объединения веток. Ветки создаются как ответвления от основной ветки master. В них можно вводить изменения, работать над различным функционалом или частями программы или файлов, а при слиянии вся изменённая информация добавляется в ветку, в которую происходит слияние. Однако в некоторых случаях возникают конфликты, например, когда изменён один и тот же файл. Если в некоторых ситуациях git самостоятельно разбирается и автоматически сливает версии в одну, где присутствует код из обеих версий, то в отдельных случаях случаются исключительные конфликты, когда нужно выбрать только что-то одно или модифицировать один из вариантов и принять его.

Для воспроизведения такого конфликта было создано две ветки: `branch_1` и `branch_2`. В обеих ветках была изменена одна и та же строка. При слиянии (merge) ветки `branch_1` проблем не возникло, слияние произошло автоматически. Однако при слиянии с `branch_2` возник merge conflict.

![](photo_dir/report_lab_6_25.png?raw=true)
![](photo_dir/report_lab_6_29.png?raw=true)
![](photo_dir/report_lab_6_33.png?raw=true)
![](photo_dir/report_lab_6_28.png?raw=true)
![](photo_dir/report_lab_6_34.png?raw=true)

При переключении в программу github desktop выводится окно, предлагающее решить конфликт слияния. Для сложных файлов решение предлагает выбрать версию файла из ветки, <u>которую</u> вливают, или из ветки, <u>в которую</u> происходит слияние.

![](photo_dir/report_lab_6_35.png?raw=true)
![](photo_dir/report_lab_6_36.png?raw=true)

Для файлов с текстом или кодом же предлагается открыть их в редакторе для просмотра конфликта.

![](photo_dir/report_lab_6_37.png?raw=true)
![](photo_dir/report_lab_6_38.png?raw=true)

После решения всех конфликтов будет доступно продолжение слияния.

![](photo_dir/report_lab_6_39.png?raw=true)

#### 3.10 Удаление побочной ветки после слияния

Для удаления веток используется команда `git branch <имя ветки> -d`. Если ввести просто `git branch`, то можно получить список всех веток, при этом активная ветка будет выделена.

![](photo_dir/report_lab_6_48.png?raw=true)

#### 3.11 Сделать изменения и зафиксировать их, оставляя комментарии, несколько раз

Вся работа по мере выполнения фиксируется при помощи функций `git add -A` и `git commit -m`. Первая функция отвечает за перенос кода (изменений) в stage - список того, что будет зафиксированно при следующем коммите. После этого зафиксированные изменения фиксируются в виде коммита второй функции с заданным комментарием.

![](photo_dir/report_lab_6_26.png?raw=true)

#### 3.12 Выполнение отката коммита

Откат комита обозначает отмену одного из зафиксированных изменений (всей пачки, зафиксированной в какой-то момент). Он выполняется при помощи `git revert`. Чтобы отменить последний коммит, нужно выбрать `git revert HEAD`. Здесь HEAD выступает в роли самого последнего коммита, коим и является (точнее, HEAD - ссылка на последний коммит по умолчанию).

![](photo_dir/report_lab_6_46_revert.png?raw=true)
![](photo_dir/report_lab_6_47_revert.png?raw=true)

#### 3.13 Создание ветки для отчёта

Командой `git branch report` создаётся ветка `report`. При помощи команды `git checkout report` выполняется переключение на неё.

![](photo_dir/report_lab_6_45.png?raw=true)

После выполнения всех изменений ветку можно отправить на удалённый репозиторий командой `git push origin report`. Таким образом, в основном репозитории будет создана ветка.

![](photo_dir/report_lab_6_49.png?raw=true)

Ветка теперь виднеется в GitHub

![](photo_dir/report_lab_6_50.png?raw=true)

#### 3.14 Оформление отчёта в файле README.md

Весь отчёт оформляется в README.md. README - файл, которые зачастую автоматически читается GitHub и выводится на основной странице. Расширение md - формат файла markdown, который обладает своими особенностями и позволяет писать текст с большей настройкой, такой как вставка изображений, подчёркивания или ссылки.

#### 3.14.1 Лог команд

```
  233  git config user.name
  234  git config --global user.name "4314 Pahomchik N.A."
  235  git config user.name
  236  git config user.email
  237  cd
  238  dir
  239  cd F:
  240  mkdir lab_6
  241  cd lab_6
  242  git clone https://github.com/NeonNik2245/LR6_N_A
  250  cd LR6_N_A/
  251  git pull
  252  git log
  256  git add -A
  257  git status
  258  git commit -m "Add a headers, started working with VS"
  259  git push origin
  260  git branch branch_1
  261  git branch branch_2
  262  git branch
  263  git checkout branch_1
  264  git add .
  265  git add .
  267  git checkout branch_1
  268  git branch branch_2
  269  git checkout branch_2
  270  git add .
  272  git add .
  273  git status
  274  git commit -m "No target commit"
  275  git checkout branch_1
  276  git add .
  277  git status
  278  git add .
  279  git status
  280  git commit -m "Commit with target"
  282  git branch
  283  git checkout branch_1
  284  git checkout branch_1
  285* git checkout
  286  git checkout branch_1 -f
  287  git merge branch_1
  288  git checkout master
  289  git merge branch_1
  290  git checkout branch_2
  291  git checkout master
  292  git merge branch_2
  293  git merge branch_2
  294  git status
  295  git push origin
  299  cat > .gitignore.txt
  300  git add -A
  301  git commit -m "Added gitignore file"
  302  git pull origin
  303  git add -A
  304  git push origin
  305  history
  306  git branch report
  307  git checkout report
  308  git add -A
  309  git commit -m "Добавлен текст в Задания"
  310  git add .
  311  git commit -m "Недоделанный коммит"
  312  git checkout
  313  git checkout
  314  git checkout HEAD~1
  315  git switch -
  316  git revert HEAD~1
  317  git revert --abort
  318  git revert HEAD
  319  git status
  320  git status
  321  git add -A
  322  git commit "Added photo_dir"
  323  git commit -m "Added photo_dir"
  324  git branch
  325  git branch branch_1 -d
  326  git branch branch_2 -d
  327  git branch
  328  git add -A
  329  git commit -m "First big part of work"
  330  git push origin report
  331  git log
  332  git history
  333  history
```



#### 3.15 Получение истории операций в форматированном виде

Логи, полученные командой `git log`

```
fe92013, 2024-11-25 00:03, 4314 Pahomchik N.A., First big part of work
622fe22, 2024-11-24 21:29, 4314 Pahomchik N.A., Added photo_dir
ce687e6, 2024-11-24 21:17, 4314 Pahomchik N.A., Revert "Недоделанный коммит"
63a3bbe, 2024-11-24 21:11, 4314 Pahomchik N.A., Недоделанный коммит
707f93e, 2024-11-24 21:03, 4314 Pahomchik N.A., Добавлен текст в Задания
cb1f3f2, 2024-11-24 20:12, 4314 Pahomchik N.A., Take vs_delete commit from master
9fb6d59, 2024-11-24 20:12, NeonNik2245, Delete .vs directory
37692c6, 2024-11-24 20:11, 4314 Pahomchik N.A., Added gitignore file
9100858, 2024-11-24 19:59, 4314 Pahomchik N.A., Merge branch 'branch_2'
3c263c7, 2024-11-24 19:24, 4314 Pahomchik N.A., Commit with target
0dc7eda, 2024-11-24 19:21, 4314 Pahomchik N.A., No target commit
8bf404d, 2024-11-24 19:20, 4314 Pahomchik N.A., Bad commit, no target
6c8a1de, 2024-11-24 19:03, 4314 Pahomchik N.A., Add a headers, started working with VS
dca14d2, 2024-11-24 18:30, NeonNik2245, Create my_tasks.md
921f53b, 2020-11-21 20:09, Kurtyanik, Обновление информации
c08a654, 2020-11-21 20:02, Kurtyanik, Файл создан пустым
3c6e913, 2020-11-21 19:58, Kurtyanik, Initial commit
```

## Выводы

В процессе работы были более близко рассмотрены работа с файлами markdown, его разметка, работа с git, ветками, коммитами, изменениями и конфликтами слияний. Как работа по изучению Git она демонстрирует хорошие результаты и высокую скорость освоения материала.