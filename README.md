# Домашнее задание к занятию "Резервное копирование" - Пергунов Д.В

### Задание 1
1.Написали следующую команду, которая делает зеркальное резервное копирование и исключает катологи начинающиеся с точки
```
rsync -ac --delete --progress --exclude=".*/" . /tmp/backup
```
2.Для копирования используется папка текущего пользователя, со следующими файлами.
![image](https://github.com/dimindrol/pergunovdv_backup/assets/103885836/ccf377fc-e017-420b-b19c-4a4b20e830a4)

3.Результат копирования

![image](https://github.com/dimindrol/pergunovdv_backup/assets/103885836/e6c3a2bc-088e-4339-a6cc-74478aa046ef)

4. Файла в каталоге /tmp/backup.
Как мы видим из результата скрытые каталоги, не подверглись резервному копированию, как и сказано в условии задания.

![image](https://github.com/dimindrol/pergunovdv_backup/assets/103885836/d6e826b3-7d3e-48f3-a717-c4831edc805d)



### Задание 2

1. Написали скрипт для регулярного резервного копирования

```
#!/bin/bash
rsync -ac --delete --exclude=".*/" /home/pergunovdv/. /tmp/backup
if [ "$?" -eq 0 ]; then
logger "Backup WELL DONE"
else
logger "Backup Failed"
fi
```

2. Проверили работу скрипта, скрипт отрабатывается верно

![image](https://github.com/dimindrol/pergunovdv_backup/assets/103885836/55f596d8-487d-4ef5-9e4c-70d2bc9fd984)

4. Настроили Cron на резервное копирование раз день

![image](https://github.com/dimindrol/pergunovdv_backup/assets/103885836/e1afdb06-b632-4503-978f-c7be3074b46d)

5. Запись в системный лог выполняется

![image](https://github.com/dimindrol/pergunovdv_backup/assets/103885836/e2c9fa39-3160-401e-aac0-63f70df10960)

