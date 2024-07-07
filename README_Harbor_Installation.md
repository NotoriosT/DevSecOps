

1. **Baixar e descompactar o instalador do Harbor:**
   ```bash
   $ cd /home/ubuntu
   $ wget https://github.com/goharbor/harbor/releases/download/v2.1.2/harbor-online-installer-v2.1.2.tgz
   $ tar -zxvf harbor-online-installer-v2.1.2.tgz
   ```

2. **Configurar o Harbor:**
   ```bash
   $ cd harbor
   $ cp ./harbor.yml.tmpl ./harbor.yml
   ```

3. **Editar o arquivo `harbor.yml` para configurar o HTTPS e o hostname:**
   - Altere o `hostname` para o nome do seu domínio ou IP.
   - Configure as opções de HTTPS conforme necessário. Consulte a [documentação oficial](https://goharbor.io/docs/2.1.0/install-config/configure-yml-file/) para detalhes.

4. **Instalar o Harbor com o scanner de vulnerabilidades Clair:**
   ```bash
   $ ./install.sh --with-clair
   ```

5. **Configurações iniciais no Harbor:**
   - Acesse o Harbor em seu navegador (use o domínio/IP configurado).
   - Faça login com as credenciais padrão:
     - Usuário: `admin`
     - Senha: `Harbor12345`
   - Crie um novo usuário e um projeto.
   - Dê permissão ao seu usuário para enviar imagens para o projeto.

6. **Habilitar o scanner de vulnerabilidades:**
   Consulte a [documentação](https://goharbor.io/docs/1.10/administration/vulnerability-scanning/) para habilitar e configurar o scanner de vulnerabilidades no Harbor.

### Referências
- [Configuração do arquivo YML do Harbor](https://goharbor.io/docs/2.1.0/install-config/configure-yml-file/)
- [Habilitar scanner de vulnerabilidades](https://goharbor.io/docs/1.10/administration/vulnerability-scanning/)
- [Executar o script de instalação](https://goharbor.io/docs/1.10/install-config/run-installer-script/)
