
# Instalação do GitLab com Docker Compose

Este guia descreve os passos necessários para instalar o GitLab usando Docker Compose, com um volume montado no diretório `/data` para armazenamento persistente.

## Pré-requisitos

- Docker
- Docker Compose

## Passos de Instalação

### 1. Instalar Docker e Docker Compose

Siga as instruções oficiais para instalar o Docker e o Docker Compose:

- [Instalação do Docker](https://docs.docker.com/get-docker/)
- [Instalação do Docker Compose](https://docs.docker.com/compose/install/)

### 2. Editar o arquivo `docker-compose.yml`

Edite o arquivo `docker-compose.yml` no repositório para configurar o GitLab conforme necessário.

### 3. Criar o volume e iniciar o contêiner

Navegue até o diretório onde o arquivo `docker-compose.yml` está localizado e execute os seguintes comandos:

```bash
docker-compose up -d
```

Este comando irá criar e iniciar o contêiner GitLab em segundo plano.

### 4. Verificar a instalação

Após alguns minutos, o GitLab estará disponível no endereço configurado. Abra o navegador e acesse este endereço para completar a configuração inicial do GitLab.

## Considerações Adicionais

- **Configuração de DNS:** Certifique-se de que o hostname esteja resolvendo para o IP do seu servidor. Se estiver testando localmente, você pode adicionar uma entrada no arquivo `/etc/hosts`.
  
  ```bash
  sudo echo "127.0.0.1 gitlab.example.com" >> /etc/hosts
  ```

- **Configuração do Firewall:** Verifique se as portas 80, 443 e 2224 estão abertas no seu firewall para permitir o acesso ao GitLab.

- **Armazenamento Persistente:** O volume `/data` garante que os dados do GitLab sejam persistentes e não sejam perdidos quando o contêiner for recriado ou parado.

## Manutenção

### Parar o contêiner

Para parar o contêiner GitLab, execute:

```bash
docker-compose down
```

### Reiniciar o contêiner

Para reiniciar o contêiner GitLab, execute:

```bash
docker-compose up -d
```

### Atualizar o GitLab

Para atualizar o GitLab, pare o contêiner, puxe a última versão da imagem e reinicie o contêiner:

```bash
docker-compose down
docker-compose pull
docker-compose up -d
```
