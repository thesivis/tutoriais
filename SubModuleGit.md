


# Comandos para trabalhar com git submodule

## Adicionando um submodulo no projeto git

Na pasta raiz de todos os repositórios digite:

```
git submodule add <URL.git>
```

## Realizando o pull recursivo
```
git pull --recurse-submodules
```

## Realizando o push recursivo
Para isso realize o commit em cada repositório, depois vá para o repositório pai e digite:

```
git status
git add *
git commit -m "Comentario"
git push --recurse-submodules=on-demand
```