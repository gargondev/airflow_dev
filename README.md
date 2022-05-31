# Instruções Básicas e Conceitos


## Configurações utilizadas no WSL2 Windows/Ubuntu

1. Verificar sua instalação do python
    * comando python -V ou python3 -V = python = "^3.10"

2. Recomendado criar ambiente virtual
    * Instalar o Poetry para gerenciamento de [dependencias](https://blog.pronus.io/posts/python/gerenciamento-de-versoes-ambiente-virtuais-e-dependencias-com-pyenv-e-poetry/)
    * Instalar dependencias com poetry install
  
3. Caso não queira usar o poetry verificar dependencias instaladas no arquivo pyproject.toml e instalar conforme sua preferencia.
   
4. Configurando AirFlow
    * ```mkdir -p ./dags ./logs ./plugins```
    * ```echo -e "AIRFLOW_UID=$(id -u)" > .env```
    * ```echo -e "AIRFLOW_GID=0" >> .env ```
  
5. Iniciando Airflow
    * Build DockerCompose = ```docker-compose up airflow-init```
    * Start Aplicação = ```docker-compose up -d```

6. Acessando aplicação
    * http://localhost:8080
    * Senha e Login = airflow
    * Todos os containers precisam estar com status healthy para aplicação estar acessível acompanhe com comando ```docker ps```

7. Primeira Dag
    * Mova o arquivo hello_operator.py para dags

