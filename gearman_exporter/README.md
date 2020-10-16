## [Gearman Exporter](https://github.com/bakins/gearman-exporter)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/gearman_exporter`
* Загружаем [последний стабильный релиз Gearman exporter](https://github.com/bakins/gearman-exporter/releases) `wget https://github.com/bakins/gearman-exporter/releases/download/v*.*.*/gearman-exporter.linux.amd64`
* Помещаем файл в рабочую директорию `mv gearman-exporter.linux.amd64 /var/lib/prometheus/gearman_exporter/`
* Назначаем исполняемые права на файл `chmod +x /var/lib/prometheus/gearman_exporter/gearman-exporter.linux.amd64`
* Помещаем [файл демона процесса](https://github.com/shidenko97/prometheus-client-instruction/blob/master/gearman_exporter/gearman_exporter.service) в директорию `/usr/lib/systemd/system/` и запускаем с автозагрузкой `systemctl enable --now gearman_exporter.service`
* Открыть порт `9418` для `tcp` соединения с сервера Prometheus
* Импортировать содержимое [файла панели gearman](https://grafana.com/api/dashboards/11423/revisions/3/download) как новая панель в Grafana

Примечания: 
- `*.*.*` необходимо заменить желаемой/актуальной версией продукта