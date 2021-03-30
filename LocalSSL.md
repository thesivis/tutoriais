


# Comandos para trabalhar com SSL local e django

## Adicionando o stunnel

Instale:

```
apt-get install stunnel4
```

## Crie uma pasta dentro do projeto django

A pasta deverá ficar junto com o arquivo manager.py

```
mkdir stunnel
```

Depois entre na pasta

```
cd stunnel
```

Vamos agora criar o certificado para teste:

```
openssl genrsa 1024 > stunnel.key
openssl req -new -x509 -nodes -sha1 -days 365 -key stunnel.key > stunnel.cert
cat stunnel.key stunnel.cert > stunnel.pem
```

Agora vamos criar um arquivo, onde iremos colocar as configurações para rodar o SSL no projeto django:

```
pid=

cert = stunnel/stunnel.pem
foreground = yes
output = stunnel.log

[https]
accept=8443
connect=8001
TIMEOUTclose=1
```

Nesta configuração iremos receber a conexão na porta 8443 e redirecionar para a 8001, que será a porta que o django estará estudando configurado para HTTPS

Volte uma pasta

```
cd ..
```

Start 3 terminais para teste

Para rodar o stunnel
```
stunnel4 stunnel/dev_https
```

Conexão local sem https do projeto
```
python manage.py runserver
```

Conexão local com https do projeto
```
HTTPS=1 python manage.py runserver 8001
```

Ao testar o localhost:8000 será utilizado sem HTTPS
Ao testar o localhost:8443 será utilizado com HTTPS
