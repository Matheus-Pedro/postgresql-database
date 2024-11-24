![PostgreSQL + Docker](./imgs/psql+docker.png)

# Projeto Exemplo com PostgreSQL e pgAdmin

Este projeto é uma aplicação de exemplo que configura um banco de dados PostgreSQL e a interface gráfica pgAdmin para gerenciamento do banco de dados. Abaixo estão as instruções para configurar e rodar o projeto em seu ambiente local ou em um servidor.

## Pré-requisitos

Antes de iniciar, verifique se você tem as seguintes ferramentas instaladas em seu sistema:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Um editor de texto como [VSCode](https://code.visualstudio.com/)

## Configuração do Ambiente
1. **Clone este repositório:**

   ```bash
   git clone https://github.com/Matheus-Pedro/postgresql-database.git
   cd postgresql-database
    ```

2. **Crie um arquivo `.env` a partir do arquivo `.env-example`:**

O arquivo `.env-example` contém as variáveis de ambiente que você precisa para configurar o PostgreSQL e o pgAdmin.

Copie o conteúdo do arquivo `.env-example` para um novo arquivo `.env`:

```
cp .env-example .env
```
**Observação**: Você pode modificar os valores no arquivo `.env` conforme necessário (ex.: banco de dados, usuário, senha).

## 3. Executando o Docker Compose

Use o Docker Compose para levantar os containers do PostgreSQL e pgAdmin.

```bash
docker-compose up -d
```
Isso irá inicializar os containers em segundo plano.

## 4. Acessando o pgAdmin

Após os containers estarem em funcionamento, você pode acessar o pgAdmin em [http://localhost:16543](http://localhost:16543) com as credenciais definidas no arquivo `.env`:

- **Email**: `example@example.com` (ou conforme definido no `.env`)
- **Senha**: `example_pgadmin_password` (ou conforme definido no `.env`)

## 5. Conectando ao Banco de Dados

Após entrar no pgAdmin, crie uma nova conexão para o banco de dados PostgreSQL com as seguintes informações:

- **Host**: `postgres` (nome do serviço no Docker Compose)
- **Porta**: `5432`
- **Nome do Banco de Dados**: `example`
- **Usuário**: `example_user`
- **Senha**: `example_password`

### Erros com o PgAdmin

Executar o seguinte comando caso PgAdmin não carregue:
```bash
sudo chown -R 5050:5050 ./data/pgadmin
```
## Estrutura de Diretórios

```plaintext
├── .env-example         # Exemplo de arquivo de variáveis de ambiente
├── .env                 # Arquivo de variáveis de ambiente (criado a partir do .env-example)
├── docker-compose.yml   # Arquivo de configuração do Docker Compose
├── README.md            # Este arquivo
```

## Arquivos Importantes

- **.env-example**: Arquivo de exemplo contendo as variáveis de ambiente.
- **docker-compose.yml**: Arquivo de configuração do Docker Compose que define os containers do PostgreSQL e pgAdmin.

<!-- ## Licença

Este projeto está licenciado sob a [MIT License](LICENSE). -->
