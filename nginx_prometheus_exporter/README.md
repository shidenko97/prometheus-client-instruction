## [NGINX Prometheus Exporter](https://github.com/nginxinc/nginx-prometheus-exporter)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/nginx_prometheus_exporter`
* Загружаем [последний стабильный релиз NGINX Prometheus Exporter](https://github.com/nginxinc/nginx-prometheus-exporter/releases) `wget https://github.com/nginxinc/nginx-prometheus-exporter/releases/download/v*.*.*/nginx-prometheus-exporter-*.*.*-linux-amd64.tar.gz`
* Распаковываем содержимое архива `tar xvf nginx-prometheus-exporter-*.*.*-linux-amd64.tar.gz` 
* Помещаем распакованные файлы в рабочую директорию `mv nginx-prometheus-exporter/* /var/lib/prometheus/nginx_prometheus_exporter/`
* Помещаем [файл демона процесса](https://github.com/shidenko97/prometheus-client-instruction/blob/master/nginx_prometheus_exporter/nginx_prometheus_exporter.service) в директорию `/usr/lib/systemd/system/` и запускаем с автозагрузкой `systemctl enable --now nginx_prometheus_exporter.service`
* Открыть порт `9113` для `tcp` соединения с сервера Prometheus
* Поместить [файл stub_status конфигурации nginx](https://github.com/shidenko97/prometheus-client-instruction/blob/master/nginx_prometheus_exporter/status.conf) в директорию `/etc/nginc/conf.d` и перегрузить nginx `service nginx reload`
* Импортировать содержимое [файла панели nginx](https://raw.githubusercontent.com/nginxinc/nginx-prometheus-exporter/master/grafana/dashboard.json) как новая панель в Grafana

Примечания: 
- `*.*.*` необходимо заменить желаемой/актуальной версией продукта