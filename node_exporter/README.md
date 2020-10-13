## [Node Exporter](https://github.com/prometheus/node_exporter)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/node_exporter`
* Загружаем [последний стабильный релиз Node exporter](https://github.com/prometheus/node_exporter/releases) `wget https://github.com/prometheus/node_exporter/releases/download/v*.*.*/node_exporter-*.*.*.linux-amd64.tar.gz`
* Распаковываем содержимое архива `tar xvf node_exporter-*.*.*.linux-amd64.tar.gz`
* Помещаем распакованные файлы в рабочую директорию `mv node_exporter-*.*.*.linux-amd64/* /var/lib/prometheus/node_exporter/`
* Помещаем [файл демона процесса](https://github.com/shidenko97/prometheus-client-instruction/blob/master/node_exporter/node_exporter.service) в директорию `/usr/lib/systemd/system/` и запускаем с автозагрузкой `systemctl enable --now node_exporter.service`
* Открыть порт `9100` для `tcp` соединения с сервера Prometheus

Примечания: 
- `*.*.*` необходимо заменить желаемой/актуальной версией продукта