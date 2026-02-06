# pet-project_for_data_engineer

Для настройки окружения и запуска докера необходимо выполнить в терминале директории проекта следующие команды:

1. Добавить виртуальное окружение 
```bash
python3 -m venv venv
```

2. Запустить виртуальное окружение
```bash
source venv/bin/activate
```

3. Добавить в директорию файл `.env` со следующим содержанием:
```bash
cat > .env << 'EOF'
# Airflow
AIRFLOW_UID=50000
AIRFLOW_PROJ_DIR=.
AIRFLOW_IMAGE_NAME=apache/airflow:3.1.6

# Airflow Web UI credentials
_AIRFLOW_WWW_USER_USERNAME=airflow
_AIRFLOW_WWW_USER_PASSWORD=airflow
EOF
```

4. Выполнить команду в терминале корневой директории проекта
```bash
docker-compose up -d
```

5. Выполнить команду для установки необходимых зависимостей
```bash
pip install -r requirements.txt
```

Для настройки minio неоходимо выполнить следующие команды
1. Скачать [Клиент minio для любой ОС](https://www.min.io/download/aistor-client) или для MacOs выполнить:
```bash
brew install minio/aistor/mc
```

2. Установить соеденение с сервером minio (логин и пароль из конфигурации в Docker-compose):
```bash 
mc alias set myminio http://localhost:9000 minioadmin minioadmin
```
3. Создать пользователя:
```bash 
mc admin user add myminio mynewuser mysecretpassword
```
4. Создать backet:
```bash
mc mb myminio/prod
```
5. Создать Access Key для пользователя, сохранить access_key и secret_key (показывается только один раз) куда-нибудь до настройки AirFlow:
```bash
mc admin user svcacct add myminio mynewuser
```

Настройка AirFlow:
1. Зайти на [http://127.0.0.1:8080] и ввести логин и пароль из Docker-compose
2. Admin -> Variables -> Add Variable -> Добавить access_key и secret_key