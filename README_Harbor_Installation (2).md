
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

### Referências
- [Configuração do arquivo YML do Harbor](https://goharbor.io/docs/2.1.0/install-config/configure-yml-file/)
- [Executar o script de instalação](https://goharbor.io/docs/1.10/install-config/run-installer-script/)
