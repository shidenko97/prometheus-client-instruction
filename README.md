# Инструкция по настройке клиентских серверов для мониторинга через Prometheus + Grafana

## Первоначальная подготовка сервера
* Создаем пользователя для работы сервиса `useradd --no-create-home -s /bin/false prometheus`
* Создаем директорию для работы скриптов `mkdir -p /var/lib/prometheus/`
* Назначаем пользователю права на директорию `chown -R prometheus:prometheus /var/lib/prometheus/`

## Другие экспортеры данных
* [Node Exporter](https://github.com/shidenko97/prometheus-client-instruction/blob/master/node_exporter/README.md) - нативный сервис для мониторинга сервера
* [NGINX Prometheus Exporter](https://github.com/shidenko97/prometheus-client-instruction/blob/master/nginx_prometheus_exporter/README.md) - сервис для мониторинга Nginx
* [Gearman Exporter](https://github.com/shidenko97/prometheus-client-instruction/blob/master/gearman_exporter/README.md) - сервис для мониторинга Gearman
* [Push Gateway](https://github.com/shidenko97/prometheus-client-instruction/blob/master/push_gateway/README.md) - шлюз для получения данных по API и транслирования их в Prometheus


