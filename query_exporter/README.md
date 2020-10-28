## [Query Exporter](https://github.com/albertodonato/query-exporter)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/query_exporter`
* Открыть порт `9560` для `tcp` соединения с сервера Prometheus
* Добавить файл конфигурации `config.yaml` в директорию `/var/lib/prometheus/query_exporter`
* Запустить docker контейнер с обработчиком `docker run -d --restart=always -p 9560:9560/tcp -v /var/lib/prometheus/query_exporter/config.yaml:/config.yaml -it adonato/query-exporter:latest`
