## [PHP-FPM Exporter](https://github.com/hipages/php-fpm_exporter)
* Создаем директорию для работы `mkdir -p /var/lib/prometheus/php_fpm_exporter`
* Загружаем [последний стабильный релиз PHP-FPM Exporter](https://github.com/hipages/php-fpm_exporter/releases) `wget https://github.com/hipages/php-fpm_exporter/releases/download/v*.*.*/php-fpm_exporter_*.*.*_linux_amd64`
* Помещаем распакованные файлы в рабочую директорию `mv php-fpm_exporter_*.*.*_linux_amd64 /var/lib/prometheus/php_fpm_exporter/`
* Помещаем [файл демона процесса](https://github.com/shidenko97/prometheus-client-instruction/blob/master/php_fpm_exporter/php_fpm_exporter.service) в директорию `/usr/lib/systemd/system/` и запускаем с автозагрузкой `systemctl enable --now php_fpm_exporter.service`
* Открыть порт `9253` для `tcp` соединения с сервера Prometheus
* Включить страницу проверки статуса php-fpm строкой `pm.status_path = /status` в файле `/etc/php-fpm.d/www.conf` и перегрузить php-fpm `service php-fpm restart`
* Импортировать содержимое [файла панели php-fpm для kubernetes](https://grafana.com/api/dashboards/4912/revisions/1/download) как новая панель в Grafana

Примечания: 
- `*.*.*` необходимо заменить желаемой/актуальной версией продукта