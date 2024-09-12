# Airflow Project with Docker Compose

Este projeto configura o Apache Airflow utilizando Docker Compose. Ele inclui os principais serviços necessários para executar o Airflow, como Webserver, Scheduler, Worker, Triggerer, Redis (para Celery), e PostgreSQL (para armazenamento de metadados).

## Estrutura do Projeto

- **dags/**: Contém os DAGs do Airflow.
- **logs/**: Diretório para logs gerados pelo Airflow.
- **plugins/**: Diretório para plugins personalizados do Airflow.
- **docker-compose.yml**: Arquivo de configuração do Docker Compose para o projeto.

# Como executar

## 1. Iniciar o ambiente Docker

Para iniciar o Airflow e seus serviços, execute o comando abaixo no diretório do projeto:
`docker-compose up -d`
Esse comando iniciará todos os containers em segundo plano.

## 2. Acessar a interface do Airflow

Depois que os serviços estiverem rodando, você poderá acessar a interface web do Airflow em:
`http://localhost:8080`
As credenciais de login padrão são:

- Usuário: airflow
- Senha: airflow

## 3. Verificar a saúde dos serviços

Você pode verificar se todos os serviços estão rodando corretamente com o seguinte comando:

`docker ps`

# Health Checks

O Docker Compose está configurado para verificar a saúde dos serviços como o Airflow Webserver, Scheduler, Worker, Redis e PostgreSQL. Se algum serviço falhar, o Docker tentará reiniciá-lo automaticamente.
