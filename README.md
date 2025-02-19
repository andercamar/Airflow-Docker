# Airflow Docker Setup

Este repositório contém a configuração de um ambiente Docker para o Apache Airflow, utilizando Docker Compose, com integração com Redis e PostgreSQL.

## Estrutura do Projeto

O projeto segue a seguinte estrutura de diretórios e arquivos:

- **`docker-compose.yaml`**  
  Arquivo de configuração do Docker Compose. Ele define os serviços necessários para rodar o Airflow, como o Airflow Web Server, Scheduler, Workers, Redis e PostgreSQL.

- **`Dockerfile`**  
  Arquivo usado para criar a imagem Docker personalizada do Airflow. Ele especifica como o Airflow será configurado e executado dentro do contêiner.

- **`requirements.txt`**  
  Arquivo com as dependências Python que precisam ser instaladas no contêiner, incluindo pacotes essenciais para a execução do Airflow.

- **`.env`**  
  Arquivo de variáveis de ambiente usado para configurar a execução do Docker Compose. Ele define configurações como credenciais do banco de dados, variáveis do Airflow e parâmetros do Redis.

## Como Configurar e Rodar os Contêineres

### 1. Configure as Variaveis de Ambiente

 - Copie o arquivo .env-example para .env, que contém as variáveis de ambiente padrão necessárias para o funcionamento do Airflow:
```bash
cp .env-example .env
```
 - Depois de copiar, você pode editar o arquivo .env para ajustar as configurações conforme necessário.

### 2. Construir a Imagem Docker

- Configurar a versão do docker no arquivo **Dockerfile** (Latest é a ultima versão disponivel)
```bash
FROM apache/airflow:latest
```
- Você precisa construir a imagem Docker a partir do **Dockerfile**:

```bash
docker build -t airflow-docker .
```
- Isso cria uma imagem com o nome **`airflow-docker`**

### 3. Subir os Contêineres

- Depois de construir a imagem, use o seguinte comando para iniciar os contêineres definidos no docker-compose.yml:
  ```bash
  docker-compose up -d
  ```
- Este comando irá iniciar os contêineres em segundo plano, baseados na configuração do Docker Compose.
