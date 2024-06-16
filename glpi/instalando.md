# Instalando GLPI

![Banner GLPI](/glpi/images/bannerglpi.png)

## Contextualização

O ambiente ao qual será instalado o serviço do glpi será em uma máquina virtual com 2 gigas de ram e com 12 gigas de armazenamento com o sistema operacional Ubuntu 22.04.4 LTS. Caso não saiba como criar seu servidor acesse [Instalando Ubuntu server](https://github.com/Elvis-Almeida/Elvis-Almeida-Ser.vidor-Linux/wiki/02.-Instalando-servidor).

## Download

Para iniciarmos basta fazer o download do software no site oficial [glpi-project.org/downloads/](https://glpi-project.org/downloads/) ou por esse [link direto](https://github.com/glpi-project/glpi/releases/download/10.0.15/glpi-10.0.15.tgz).

Com o link devidamente copiado podemos usar o comando para baixarmos diretamente no servidor:

```bash
wget https://github.com/glpi-project/glpi/releases/download/10.0.15/glpi-10.0.15.tgz
```

![baixando arquivos](/glpi/images/baixando.png)

## Extraindo arquivos

Com o download concluído vamos na pasta onde o download foi feito que no meu caso foi na pasta `/var/www/html` onde deve ficar os arquivos para o servidor web apache possa executar o software, caso você não tenha instalado e configurado um servidor web acesse [Instalando servidor web](<https://github.com/Elvis-Almeida/Elvis-Almeida-Servidor-Linux/wiki/05.-Servidor-Web-(Apache)>), estando na pasta correta vamos extrair os arquivos com o comando:

```bash
tar -xf glpi-10.0.15.tgz
```

![extraindo arquivos](/glpi/images/extraindo.png)

Após a extração é criada a pasta glpi onde contém todos os arquivos do software e como ela já foi extraida dentro da pasta do servidor web não precisamos move-la

## Aplicando permissões

Agora vamos executar dois comandos para darmos as permissõoes necessárias para o funcionamento do software que são:

```bash
chown -R www-data:www-data glpi
chmod -R 755 glpi
```

Onde `chown -R www-data:www-data glpi` altera o proprietário e o grupo de todos os arquivos e subdiretórios dentro do diretório glpi para www-data e
`chmod -R 755 glpi` define as permissões de todos os arquivos e subdiretórios dentro do diretório glpi para 755, o que significa que o proprietário tem permissões de leitura, escrita e execução, enquanto o grupo e outros têm permissões de leitura e execução.

## Instalando dependências

Agora vamos instalar as dependências para que o GLPI funcione corretamente com o comando:

> ⚠️ Atenção! execute `apt update && apt upgrade` para atualizar tudo envitando erros.

```bash
apt install php libapache2-mod-php php-mysql php-curl php-gd php-intl php-ldap php-apcu php-xml php-zip php-imap php-mbstring mariadb-server mariadb-client php-bz2 php-gd
```

![Instalando dependencias](/glpi/images/instalandoDependencias.png)

Este comando faz o download de:

> PHP: Linguagem de programação para scripts do lado do servidor.

> MariaDB: Banco de dados relacional.

> Extensões PHP: Suporte adicional para funcionalidades como bancos de dados, manipulação de imagens, internacionalização, cache, etc.

## Configurando banco de dados

Agora vamos configurar o banco de dados para que seja usado pelo glpi

> ⚠️ Atenção! as configurações seguintes serão de ambiente de teste somente, para configurar para produção existem passos importantes que não são mensionados aqui.

Como o banco de dados já foi instalado com o comando anterior vamos fazer a configuração inicial usando:

```bash
mysql_secure_installation
```

![configurando banco de dados](/glpi/images/configurandoBandoDeDados.png)

Após completar todos esses passos, sua instalação do MariaDB está mais segura, essa foi as mudanças principais que fiz:

- Senha do root definida ou atualizada.
- Usuários anônimos removidos.
- Login remoto para o usuário root desabilitado.
- Banco de dados de teste removido.
- Privilégios recarregados para aplicar todas as mudanças.

Após isso agora vamos criar nossa `database` para o glpi e seu devido usuário.

Vamos acessar o MariaDb usando o comando e digitando a senha criada anteriormente:

```bash
mysql -u root -p
```

![acessando MariaDb](/glpi/images/acessandoMariaDb.png)

Dentro do MariaDb vamos usar o comando sequinte para criar a `database` do glpi:

```sql
create database glpi;
```

![criando database](/glpi/images/createDatabase.png)

Com a `database` criada vamos criar o usuário com o sequinte comando:

```sql
create user 'glpi'@'localhost' identified by '123';
```

![criando usuario da database](/glpi/images/createuserdatabase.png)

Com esse comando criamos o usuário glpi com a senha 123

Agora vamos da todos os privilegios para esse usuário com o comando:

```sql
grant all privileges on glpi.* to 'glpi'@'localhost';
```

Com o usuário devidamente permitido agora vamos atualizar as tabelas para que tudo seja carregado com o comando:

```sql
flush privileges;
```

![atualizando permissões](/glpi/images/flushPrivileges.png)

Com o banco de dados configurado agora vamos para a etapa final de instalação

## Etapa final de instalação

Agora vamos acessar nosso servidor web, é só em seu navegador colocar o ip do servidor e o caminho /glpi que é a pasta onde está o GLPI, no meu caso acessei `10.0.0.2/glpi` onde chegamos na tela de escolher o idioma.

Aqui é só escolher o idioma e proseguir:

![escolhendo idioma](/glpi/images/EscolherIdioma.png)

Essa proxima tela é para aceitar os termos de uso, como sei que você não vai ler também é só proseguir:

![termos de uso](/glpi/images/termosDeUso.png)

Nessa tela vamos clicar em instalar.

![Instalar ou atualizar](/glpi/images/instalarOuAtualizar.png)

Nessa outra tela vemos as dependências, se todas estão ok, observamos que algumas configurações de segurança estão pendentes, mas como nossa instalação é de teste vamos ignorar e seguir para a próxima tela.

![dependencias](/glpi/images/dependencias1.png)
![dependencias](/glpi/images/dependendias2.png)

Nessa tela vamos colocar o acesso ao banco de dados, no primeiro colocamos o endereço do banco, que no nosso caso é localhost, no segundo colocamos o usuário que criamos e após ele a senha do mesmo. Preenchido corretamente é só continuar.

![dependencias](/glpi/images/addBancoDeDados.png)

Nessa parte vamos adicionar o `database` que criamos antriormente, basta selecionar ele e continuar

![dependencias](/glpi/images/selecionandoDatabase.png)

Nessa parte ele pergunta se você quer enviar dados de estatistica de uso, fica a seu critério, clique em continuar.

![dependencias](/glpi/images/enviarDados.png)

Nessa tela aparece alguns informativos, é só clicar em continuar.

![dependencias](/glpi/images/informativos.png)

Aqui você ver que a instalação foi concluida e ele mostra os usuários padrões que você já pode usar.

![dependencias](/glpi/images/instalacaoconcluida.png)

Agora finalmente chegamos à nossa tela de login, onde você já pode entrar com qual quer usuário mostrado anteriormente.

![dependencias](/glpi/images/telaDeLogin.png)

E essa é a nossa tela de Dashboad linda e zerada.

![dependencias](/glpi/images/dashboad.png)

Agora você guerrero que chegou até aqui vamos para a segunda etapa, como usar a ferramenta.
