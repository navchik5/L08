## Отчет по лабораторной работе Л08: Docker Compose + Доп. задание

### 1. Цель работы
Изучение Docker Compose для управления многоконтейнерными приложениями. Сборка стека Flask+Redis и стека мониторинга Prometheus+Grafana+Blackbox Exporter. Дополнительно: настройка сбора кастомных метрик и визуализация посещений.

### 2. Стек Flask+Redis
Создано веб-приложение на Flask, которое считает посещения и хранит их в Redis. Контейнеры запущены через docker compose up. Проверка через curl подтвердила работу счетчика.

<img width="1349" height="207" alt="image" src="https://github.com/user-attachments/assets/a351d1ce-69cf-4496-9f41-a51407b21921" />

### 3. Стек мониторинга Prometheus+Grafana
Созданы конфиги для Prometheus и Grafana. Стек запущен через docker compose.

<img width="1175" height="103" alt="image" src="https://github.com/user-attachments/assets/28c12b34-d93c-4b3b-8a5f-a86f4aeb8100" />

### 4. Blackbox Exporter
Добавлен контейнер Blackbox Exporter и настроен опрос сайтов. Проверка через curl подтвердила работу экспортера.

<img width="1141" height="238" alt="d81993f2-72fe-4f7d-b626-e907f8440c7f" src="https://github.com/user-attachments/assets/fe97380d-6ca6-469d-8c4b-5660a97f9ddc" />

### 5. Дашборд в Grafana (Blackbox)
Импортирован дашборд (ID 13659). Настроен опрос трех целей. Видно, что Flask и student.psu.ru доступны (UP), а etis.psu.ru — нет (DOWN).

<img width="1173" height="681" alt="image" src="https://github.com/user-attachments/assets/319e8824-1da8-47c7-add3-de839f2f9ae5" />

### 6. Дополнительное задание: Метрики Flask и график посещений
В Flask-приложение добавлен endpoint /metrics, отдающий метрику view_count. В Prometheus добавлен job view_total. В Grafana добавлена панель Visits per second с формулой rate(view_count[30s]).

<img width="513" height="113" alt="image" src="https://github.com/user-attachments/assets/587afc6e-8969-45b1-8b69-9ef6f79553ea" />

<img width="1283" height="87" alt="image" src="https://github.com/user-attachments/assets/553a00a9-1f6b-4060-bfde-5e5e865fbcfd" />

<img width="886" height="902" alt="image" src="https://github.com/user-attachments/assets/7bd57f58-4b48-4cac-a551-0ff96bc8b5fc" />
