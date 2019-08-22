
# Configurar jupyter como servidor

Instalação do jypyter
```
apt-get install python3-jupyter-core python3-nbconvert python3-nbformat python3-notebook
```

Criando arquivo de configuração do servidor jupyter
```
$jupyter notebook --generate-config
```

Edite as seguintes linhas do arquivo ~/.jupyter/jupyter_notebook_config.py
Neste caso liberando para qualquer IP
```
c.NotebookApp.ip = '0.0.0.0'
c.NotebookApp.notebook_dir = '<PATH>'
c.NotebookApp.port = <PORT>
```

Criando uma senha para acessar o jupyter
```
jupyter notebook password
```

Rodando o serviço sem abrir o browser por padrão

```
jupyter notebook --no-browser &
```
