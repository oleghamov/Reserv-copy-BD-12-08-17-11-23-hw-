# Домашнее задание к занятию "Резервное копирование баз данных" - `Хамов Олег`

### Задание 1

Резервное копирование

1. Необходимо восстанавливать данные в полном объёме за предыдущий день.

Для восстановления данных в полном объеме наиболее подходящий вариант резервного

копирования — это полное резервное копирование. Конечно может подойти и

дифференциальное копирование, оно будет накапливать все новые изменения, которые

произошли с момента последнего полного бекапа. Если до этого с момента последнего

копирования использовался инкрементный способ копирования, то лучше сначала сделать

полный бекап, а потом дифференцированный или инкрементный, в зависимости от объема

данных и частоты их изменений, а так же от стоимости и необходимости быстрого

восстановления данных, в случае сбоя. Дифференцированное будет обходится дороже при

большом  часто изменяющемся массиве данных, но с помощью него можно быстрее

восстановиться, а вот инкрементное будет экономичнее, в том числе и по занимаемому

месту на сервере, но оно будет более долгим в процессе восстановления.

2. Необходимо восстанавливать данные за час до предполагаемой поломки.

В случае, если необходимо восстанавливать данные за час до предполагаемой поломки, то

здесь крайне необходимо воспользоваться полным бекапом, потому что, любой другой

вариант, не позволит сохранить всю базу, что инкрементное, что дифференциальное

копирование, позволят сохранить только последние измененные данные с момента

последнего полного резервного копирования, а все остальное может потеряться.

Дифференцированное сохранить чуть больше, чем инкрементное, но все равно это будет

касаться лишь последних изменений.

### Задание 2

PostgreSQL

1. Копируем команду из папки «bin» утилиты PostgreSQL:

    pg_dump -h localhost -p 5432 -d postgres -U postgres > E:\01\backup.backup

 - Вставляем ее в консоль

 - Хост, порт, база для бэкапа, файл и формат файла выхода бэкапа могут варьироваться.

2. Что бы осуществить beckup, нужно в той же папке «bin» выполнить команду:

    pg_restore -d postgres –h localhost –p 5432 –U postgres E:\документы\SQL\db.backup

### Задание 3

MySQL

Команда инкрементного резервного копирования базы данных MySQL из официальной документации:

    mysqlbackup --defaults-file=/home/dbadmin/my.cnf \
      --incremental --incremental-base=history:last_backup \
      --backup-dir=/home/dbadmin/temp_dir \
      --backup-image=incremental_image1.bi \
       backup-to-image









