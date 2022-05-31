# Comandos para Instalação Docker AirFlow

1. Baixar docker-compose.yaml

   * `curl -LfO 'https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml'`
2. Realizar Alterações docker-compose.

   * Alterar `AIRFLOW__CORE__LOAD_EXAMPLES: 'true'` para false, para não gerar dags de exemplo.
   * Alterar variaveis admin.
     ```
     _AIRFLOW_WWW_USER_USERNAME: ${_AIRFLOW_WWW_USER_USERNAME:-airflow}
     _AIRFLOW_WWW_USER_PASSWORD: ${_AIRFLOW_WWW_USER_PASSWORD:-airflow}
     ```
3. Definir portas expose para os serviços.

   * airflow-webserver:8080:8080 default
   * postgres 5432 default
   * celery opcional
   * regis 6379 default opcional
4. Se executar a variavel como "AIRFLOW__CORE__EXECUTOR: LocalExecutor" remover os seguintes parâmetros.

   * AIRFLOW__CELERY__RESULT_BACKEND:
   * AIRFLOW__CELERY__BROKER_URL
   * redis: condition: service_healthy
   * services: redis "Remover todo conteudo do serviço redis"
   * airflow-worker "Remover todo conteudo do serviço airflow-worker"
   * flower "Remover todo conteudo do serviço flower"
5. Setar definições .env para instalação Linux.

   * Criar folders. ```mkdir -p ./dags ./logs ./plugins```
   * Criar .env ```echo -e "AIRFLOW_UID=$(id -u)" > .env```
6. Criar as imagens airflow com comando docker abaixo.

* ```docker-compose up airflow-init```

7.  Subir os container 
   * ```docker-compose up -d```

# Referencias para consultas.

* [Airflow para Produção](https://www.youtube.com/watch?v=wDr3Y7q2XoI)
