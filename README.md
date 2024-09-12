# Airflow Project with Docker Compose

Este projeto configura o Apache Airflow utilizando Docker Compose. Ele inclui os principais serviços necessários para executar o Airflow, como Webserver, Scheduler, Worker, Triggerer, Redis (para Celery), e PostgreSQL (para armazenamento de metadados).

## Estrutura do Projeto

- **dags/**: Contém os DAGs do Airflow.
- **logs/**: Diretório para logs gerados pelo Airflow.
- **plugins/**: Diretório para plugins personalizados do Airflow.
- **docker-compose.yml**: Arquivo de configuração do Docker Compose para o projeto.

# Como executar

## 1. Configurar o AIRFLOW**CORE**FERNET_KEY

Copiar o arquivo `.env.sample` para `.env`
executar os seguintes comandos:

### 1.1. Criar um novo ambiente virtual

Se o ambiente virtual não foi criado, execute o seguinte comando para criar um novo ambiente virtual chamado venv:
bash

`python3 -m venv venv`

### 1.2. Ativar o ambiente virtual

Após criar o ambiente virtual, ative-o com o seguinte comando:

No Linux/macOS:

`source venv/bin/activate`

No Windows:

`venv\Scripts\activate`

### 1.3. Instalar o módulo cryptography

Agora que o ambiente virtual está ativado, instale o módulo cryptography:

`pip install cryptography`

### 1.4. Verificar a instalação

Verifique se o módulo foi instalado corretamente:

`python3 -c "import cryptography"`

### 1.5. Gerar a chave Fernet

Agora você deve conseguir gerar a chave Fernet normalmente:

`python3 -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"`

pegar o response do codigo acima e colocar no `.env` na variavel `AIRFLOW__CORE__FERNET_KEY`

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
