# ml_lab

## Setup environment
1. Создайте .env файл в корневой директории проекта, аналогичный файлу .env.example (просто удалить .example из названия файла);

2. Поднимем minio в контейнере и установим зависимости:
 ```bash
   make setup
   ```

2. Создадим бакет и загрузим titanic.csv в minio:
 ```bash
   make upload-data
   ```

3. Обработаем titanic.csv и положим обработанный titanic_processed.csv в minio:
 ```bash
   make process-data
   ```

4. В .env нужно добавить API ключ w&b

5. Сбилдим образ для обучения 
```bash
   make build-trainer-image
```

6. Скачаем обработанные данные
```bash 
   make download processed-data
```

7. Запустим эксперементы 
```bash
   make run-experiments
```

8. Загрузим модели эксперементов в хранилище 
```bash
   make upload-results
```

P.S. На машине должен быть установлен python и poetry. Если в глобальных переменных/путях стоит python3 вместо python, то poetry может некорректно работать. Чтобы исправить, создадим символическую ссылку:
   ```bash
   sudo ln -s $(which python3) /usr/local/bin/python
   ```

В случае возникновения ошибки ModuleNotFoundError: No module named 'dotenv': 

Удалим текущее окружение:
   ```bash 
   poetry env remove python
   ```

Заново поднимем окружен: 
   ```bash
   poetry env use python3.10
   poetry install
   ```

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

A short description of the project.

## Project Organization

├── Dockerfile.train
├── Makefile
├── README.md
├── docker-compose.yml
├── lab3
│   ├── config_grid.json
│   ├── scripts
│   │   ├── create_bucket.py
│   │   ├── download_from_s3.py
│   │   ├── process_data.py
│   │   ├── run_experiment.sh
│   │   ├── train_model.py
│   │   ├── upload_experiment_results.py
│   │   └── upload_to_s3.py
│   ├── titanic.csv
│   └── titanic_processed.csv
├── mypy.ini
├── output
│   ├── 10_10_2_10_10_2_model_(10, 10, 2).pkl
│   ├── 10_10_2_10_5_2_model_(10, 5, 2).pkl
│   ├── 10_10_2_50_10_2_model_(50, 10, 2).pkl
│   ├── 10_10_2_50_5_2_model_(50, 5, 2).pkl
│   ├── 10_5_2_10_10_2_model_(10, 10, 2).pkl
│   ├── 10_5_2_10_5_2_model_(10, 5, 2).pkl
│   ├── 10_5_2_50_10_2_model_(50, 10, 2).pkl
│   ├── 10_5_2_50_5_2_model_(50, 5, 2).pkl
│   ├── 50_10_2_10_10_2_model_(10, 10, 2).pkl
│   ├── 50_10_2_10_5_2_model_(10, 5, 2).pkl
│   ├── 50_10_2_50_10_2_model_(50, 10, 2).pkl
│   ├── 50_10_2_50_5_2_model_(50, 5, 2).pkl
│   ├── 50_5_2_10_10_2_model_(10, 10, 2).pkl
│   ├── 50_5_2_10_5_2_model_(10, 5, 2).pkl
│   ├── 50_5_2_50_10_2_model_(50, 10, 2).pkl
│   └── 50_5_2_50_5_2_model_(50, 5, 2).pkl
├── poetry.lock
├── pyproject.toml
└── setup.cfg

