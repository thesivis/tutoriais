
#Configurar Ubuntu para ser o git server pelo http

Crie uma pasta onde ficará os repositórios do git
```
mkdir <PATH>/git
mkdir <PATH>/git/<REPO>.git
cd <PATH>/git/<REPO>.git
```

Inicie a pasta com o git
```
git --bare init
```

Crie o arquivo de senhas para o projeto
```
htpasswd -c /etc/apache2/<ARQ>.passwd <USER>
```

No /etc/apache2/sites-available/000-default.conf adicione os seguintes parâmetros globais:

```
        SetEnv GIT_PROJECT_ROOT <PATH>/git
        SetEnv GIT_HTTP_EXPORT_ALL
        ScriptAlias /git/ /usr/lib/git-core/git-http-backend/
```

Obs: Certifique-se da existência do arquivo /usr/lib/git-core/git-http-backend/

Crie o arquivo de configuração do apache para o seu repositório

```
conf-available/<REPO>.conf
```

```
<Location /git/<REPO>.git>
        AuthType Basic
        AuthName "Private Git Access"
        AuthUserFile /etc/apache2/<ARQ>.htpasswd
        Require valid-user
</Location>
```

Restarte o apache

```
service apache2 restart
```