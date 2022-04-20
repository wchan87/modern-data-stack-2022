# Apache Airflow

Based on [Running Airflow in Docker](https://airflow.apache.org/docs/apache-airflow/stable/start/docker.html)

1. Fetch `docker-compose.yaml`
	```bash
	curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.2.5/docker-compose.yaml'
	```
2. Create appropriate directories
	```bash
	mkdir -p ./dags ./logs ./plugins
	echo -e "AIRFLOW_UID=$(id -u)" > .env
	```
3. Initialize database
	```bash
	docker-compose up airflow-init
	```
4. Run Airflow
	```bash
	docker-compose up
	```

Default login created is `airflow/airflow`

* airflow-webserver http://localhost:8080
* flower http://localhost:5555

Start
```bash
docker-compose start
```

Stop
```bash
docker-compose stop
```

Cleanup
```bash
docker-compose down --volumes --rmi all
```

## Airflow CLI

1. Fetch `airflow.sh`
	```bash
	curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.2.5/airflow.sh'
	chmod +x airflow.sh
	```
2. Run commands like
	```bash
	./airflow.sh info
	./airflow.sh bash
	./airflow.sh python
	```

## Airflow REST API

```bash
ENDPOINT_URL="http://localhost:8080/"
curl -X GET --user "airflow:airflow" "${ENDPOINT_URL}/api/v1/pools"
```
