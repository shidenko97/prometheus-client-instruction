## [Push Gateway](https://github.com/prometheus/pushgateway)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/push_gateway`
* Загружаем [последний стабильный релиз Push Gateway](https://github.com/prometheus/pushgateway/releases) `wget https://github.com/prometheus/pushgateway/releases/download/v*.*.*/pushgateway-*.*.*.linux-amd64.tar.gz`
* Распаковываем содержимое архива `tar xvf pushgateway-*.*.*.linux-amd64.tar.gz` 
* Помещаем файл в рабочую директорию `mv pushgateway /var/lib/prometheus/push_gateway/`
* Помещаем [файл демона процесса](https://github.com/shidenko97/prometheus-client-instruction/blob/master/push_gateway/push_gateway.service) в директорию `/usr/lib/systemd/system/` и запускаем с автозагрузкой `systemctl enable --now push_gateway.service`
* Открыть порт `9091` для `tcp` соединения с сервера Prometheus

Примечания: 
- `*.*.*` необходимо заменить желаемой/актуальной версией продукта