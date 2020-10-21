## [MySQL Exporter](https://github.com/prometheus/mysqld_exporter)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/mysql_exporter`
* Загружаем [последний стабильный релиз MySQL Exporter](https://github.com/prometheus/mysqld_exporter/releases) `wget https://github.com/prometheus/mysqld_exporter/releases/download/v*.*.*/mysqld_exporter-*.*.*.linux-amd64.tar.gz`
* Распаковываем содержимое архива `tar xvf mysqld_exporter-*.*.*.linux-amd64.tar.gz` 
* Помещаем распакованные файлы в рабочую директорию `mv mysqld_exporter-*.*.*.linux-amd64/* /var/lib/prometheus/mysql_exporter/`
* Создаем в MySQL локального пользователя для работы с экспортом c помощью команд `CREATE USER 'exporter'@'localhost' IDENTIFIED BY '{password}' WITH MAX_USER_CONNECTIONS 3;` и `GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'localhost';`
* Помещаем [файл конфигурации](https://github.com/shidenko97/prometheus-client-instruction/blob/master/mysql_exporter/my.cnf) в директорию `/var/lib/prometheus/mysql_exporter/`
* Помещаем [файл демона процесса](https://github.com/shidenko97/prometheus-client-instruction/blob/master/mysql_exporter/mysqld_exporter.service) в директорию `/usr/lib/systemd/system/` и запускаем с автозагрузкой `systemctl enable --now mysqld_exporter.service`
* Открыть порт `9104` для `tcp` соединения с сервера Prometheus
* Импортировать содержимое [файла панели MySQL](https://grafana.com/api/dashboards/6239/revisions/1/download) как новая панель в Grafana

Примечания: 
- `*.*.*` необходимо заменить желаемой/актуальной версией продукта
- `{password}` необходимо сгенерировать для создания пользователя и вставить в файле конфигурации `my.cnf`