## 1. Введение

Это руководство описывает процесс установки инструментов мониторинга и визуализации: Grafana, Prometheus, Node Exporter и VictoriaMetrics. Эти инструменты позволяют создавать мощную систему мониторинга для анализа и визуализации метрик.

## 2. Установка Prometheus
Шаги:

    Скачайте последнюю версию Prometheus с официального сайта:

wget https://github.com/prometheus/prometheus/releases/download/v2.x.x/prometheus-2.x.x.linux-amd64.tar.gz

Распакуйте загруженный архив:
```
tar -xvzf prometheus-2.x.x.linux-amd64.tar.gz
cd prometheus-2.x.x.linux-amd64
```
Запустите Prometheus с файлом конфигурации:
```
    ./prometheus --config.file=prometheus.yml

    Настройте файл prometheus.yml для корректной работы (по умолчанию можно использовать базовую конфигурацию).
```
## 3. Установка Node Exporter
Шаги:

    Загрузите Node Exporter с страницы загрузки Prometheus:

wget https://github.com/prometheus/node_exporter/releases/download/vX.X.X/node_exporter-X.X.X.linux-amd64.tar.gz

Разархивируйте файл:
```
tar -xvzf node_exporter-X.X.X.linux-amd64.tar.gz
cd node_exporter-X.X.X.linux-amd64
```
Запустите Node Exporter командой:
```
    ./node_exporter

    Проверьте его доступность по адресу http://localhost:9100/metrics.
```
## 4. Установка VictoriaMetrics
Шаги:
```
    Скачайте VictoriaMetrics с официального сайта:

wget https://github.com/VictoriaMetrics/VictoriaMetrics/releases/download/vX.X.X/victoria-metrics-linux-amd64-vX.X.X.tar.gz
```
Извлеките содержимое:
```
tar -xvzf victoria-metrics-linux-amd64-vX.X.X.tar.gz
cd victoria-metrics-linux-amd64
```
Запустите VictoriaMetrics:
```
./victoria-metrics-prod -retentionPeriod=1 -storageDataPath=/path/to/data
```
Настройте Prometheus для отправки метрик в VictoriaMetrics, добавив в prometheus.yml следующую секцию:
```
    remote_write:
      - url: "http://localhost:8428/api/v1/write"
```
## 5. Установка Grafana
Шаги:

    Добавьте репозиторий и установите Grafana:
```
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo apt-get update
sudo apt-get install grafana
```
Запустите службу Grafana:
```
    sudo systemctl start grafana-server
    sudo systemctl enable grafana-server
```
    Перейдите к интерфейсу Grafana по адресу http://localhost:3000 (по умолчанию используйте логин admin и пароль admin).
    Настройте источники данных, перейдя в "Configuration" > "Data Sources" и добавив Prometheus или VictoriaMetrics.

## 6. Интеграция компонентов

    Настройте Prometheus для сбора метрик с Node Exporter, добавив в prometheus.yml следующую конфигурацию:
```
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```
В Grafana создайте визуализационные панели (дашборды) для отображения метрик, собранных Prometheus или VictoriaMetrics.


### Визуальная панель графаны:


<img width="1440" alt="изображение" src="https://github.com/user-attachments/assets/c962797e-7838-40c6-a36c-1d01b0c49929">


## Файл Docker-compose.yaml

<img width="1080" alt="изображение" src="https://github.com/user-attachments/assets/2f509582-5ffc-4e1e-8682-9601d1af5ef1">



<img width="1080" alt="изображение" src="https://github.com/user-attachments/assets/f09d91e2-6eb7-4f1f-bf08-e6f28e0947ad">



<img width="1080" alt="изображение" src="https://github.com/user-attachments/assets/ee7135c5-4cad-4d1a-a229-31779ac08868">


<img width="1080" alt="изображение" src="https://github.com/user-attachments/assets/3be85b2a-39b0-4b84-8c3b-15eb73469754">



## Файл Prometheus.yaml


<img width="1080" alt="изображение" src="https://github.com/user-attachments/assets/93aaa720-30a9-48f4-94eb-e642045000a4">



# Результат Nmap


<img width="1080" alt="изображение" src="https://github.com/user-attachments/assets/58d0a8f6-5ba7-42c6-9572-29565513de3a">

