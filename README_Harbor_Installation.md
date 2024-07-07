
### Instalação e Configuração do Harbor com HTTPS e Scanner de Vulnerabilidades

Este guia descreve os passos para instalar e configurar o Harbor em um servidor Ubuntu, habilitando o HTTPS e o scanner de vulnerabilidades.

#### Passos para Instalação

1. **Acesse o servidor:**
   ```bash
   $ ssh -i curso.pem ubuntu@3.239.91.96
   ```

2. **Instalar Docker:**
   ```bash
   $ sudo su
   $ curl https://releases.rancher.com/install-docker/19.03.sh | sh
   $ usermod -aG docker ubuntu
   ```

3. **Instalar Docker Compose:**
   ```bash
   $ apt-get install git -y
   $ curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   $ chmod +x /usr/local/bin/docker-compose
   $ ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
   ```

4. **Baixar e descompactar o instalador do Harbor:**
   ```bash
   $ cd /home/ubuntu
   $ wget https://github.com/goharbor/harbor/releases/download/v2.1.2/harbor-online-installer-v2.1.2.tgz
   $ tar -zxvf harbor-online-installer-v2.1.2.tgz
   ```

5. **Configurar o Harbor:**
   ```bash
   $ cd harbor
   $ cp ./harbor.yml.tmpl ./harbor.yml
   ```

6. **Editar o arquivo `harbor.yml` para configurar o HTTPS e o hostname:**
   - Altere o `hostname` para o nome do seu domínio ou IP.
   - Configure as opções de HTTPS conforme necessário. Consulte a [documentação oficial](https://goharbor.io/docs/2.1.0/install-config/configure-yml-file/) para detalhes.

7. **Instalar o Harbor com o scanner de vulnerabilidades Clair:**
   ```bash
   $ ./install.sh --with-clair
   ```

8. **Configurações iniciais no Harbor:**
   - Acesse o Harbor em seu navegador (use o domínio/IP configurado).
   - Faça login com as credenciais padrão:
     - Usuário: `admin`
     - Senha: `Harbor12345`
   - Crie um novo usuário e um projeto.
   - Dê permissão ao seu usuário para enviar imagens para o projeto.

9. **Habilitar o scanner de vulnerabilidades:**
   Consulte a [documentação](https://goharbor.io/docs/1.10/administration/vulnerability-scanning/) para habilitar e configurar o scanner de vulnerabilidades no Harbor.

### Referências
- [Configuração do arquivo YML do Harbor](https://goharbor.io/docs/2.1.0/install-config/configure-yml-file/)
- [Habilitar scanner de vulnerabilidades](https://goharbor.io/docs/1.10/administration/vulnerability-scanning/)
- [Executar o script de instalação](https://goharbor.io/docs/1.10/install-config/run-installer-script/)
