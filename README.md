# copy


### Задание 1
1. Составьте команду rsync, которая позволяет создавать зеркальную копию домашней директории пользователя в директорию /tmp/backup
2. Необходимо исключить из синхронизации все директории, начинающиеся с точки (скрытые)
3. Необходимо сделать так, чтобы rsync подсчитывал хэш-суммы для всех файлов, даже если их время модификации и размер идентичны в источнике и приемнике.
4. На проверку направить скриншот с командой и результатом ее выполнения

rsync -ac --delete --exclude=".*/" . /tmp/backup
![резервное копирование](https://github.com/AnastasiyaEvsseva/copy/assets/151757353/bba60275-bb3c-4664-9f91-cf7c20addca4)

### Задание 2
1. Написать скрипт и настроить задачу на регулярное резервное копирование домашней директории пользователя с помощью rsync и cron.
2. Резервная копия должна быть полностью зеркальной
3. Резервная копия должна создаваться раз в день, в системном логе должна появляться запись об успешном или неуспешном выполнении операции
4. Резервная копия размещается локально, в директории /tmp/backup
5. На проверку направить файл crontab и скриншот с результатом работы утилиты.

  rsync -a --delete /home/joos/ /tmp/backup

if [ "$?" -eq 0 ]; then
        logger "Backup successfully"
else    logger "Backup failed"
fi

0 * * * * /home/joos/rsync.sh

![резервное копирование 2ъ](https://github.com/AnastasiyaEvsseva/copy/assets/151757353/977c885d-f57e-493f-8689-d91de5036a5f)
