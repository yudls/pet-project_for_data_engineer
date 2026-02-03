# pet-project_for_data_engineer

1. Добавить виртуальное окружение 
```bash
python3 -m venv venv
```
2. Запустить виртуальное окружение
```bash
source venv/bin/activate
```

3. Добавить в директорию файл `.env` со следующим содержанием:
```
# Airflow
AIRFLOW_UID=50000
AIRFLOW_PROJ_DIR=.
AIRFLOW_IMAGE_NAME=apache/airflow:3.1.6

# Airflow Web UI credentials
_AIRFLOW_WWW_USER_USERNAME=airflow
_AIRFLOW_WWW_USER_PASSWORD=airflow
```

4. Выполнить команду в терменале корневой директории проекта
```bash
docker-compose up -d
```

5. Выполнить команду для установки необходимых зависимостей
```bash
pip install -r requirements.txt
```