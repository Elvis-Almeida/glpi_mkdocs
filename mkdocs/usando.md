# Como usar o Mkdocs

![Banner GLPI](/mkdocs/images/bannermkdocs2.png)

## Criando nova documentação

Para iniciarmos vamos criar uma nova documentação para isso é muito simples basta digitarmos:

```bash
mkdocs new mkdocs
```

![nova documentacao mkdocs](/mkdocs/images/novadocumentacaomkdocs.png)

Ao executar esse comando é criado um novo diretório chamado mkdocs (ou o nome que você forneceu) e ele é criado no local onde o comando foi executado também é criado a estrutura de diretórios inicial dentro deste diretório, contendo:

- **mkdocs.yml:** O arquivo de configuração principal do MkDocs. Ele contém configurações sobre o site, como o tema, título e outras opções de configuração.

- **docs:** Um diretório que contém a documentação do projeto. Por padrão, inclui um arquivo index.md que serve como a página inicial da documentação.

## Visualização de teste

Com isso em mãos já podemos ver o que foi criado por padrão, para isso é só entrarmos na pasta e digitarmos:

```bash
mkdocs serve -a 10.0.0.2:5500
```

> ⚠️ Atenção! adicione o ip correto da sua máquina no comando.

Onde esse comando cria um servidor http na porta 5500 que servirá a página para que possamos ter uma visualização rápida do que está configurado nos arquivos.

![Banner GLPI](/mkdocs/images/mkdocspadrao.png)

Podemos ver que já é uma página bastante apresentável

## Configurando aprensentação

Agora vou apresentar algumas configurações do arquivo `mkdocs.yml` mais especificamente, as configurações que usei nesta documentação que você está lendo:

### Configuração completa

```yml
site_name: Documentação GLPI e MkDocs
nav:
  - Home: index.md
  - GLPI:
      - Instalando: glpi/instalando.md
      - Usando: glpi/usando.md
  - MkDocs:
      - Instalando: mkdocs/instalando.md
      - Usando: mkdocs/usando.md
theme:
  name: material
  language: pt-BR
  custom_dir: overrides
  logo: logo.png
  favicon: logo.png
  palette:
    - media: "(prefers-color-scheme: light)"
      scheme: default
      primary: grey
      accent: indigo
      toggle:
        icon: material/lightbulb
        name: Modo claro
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      primary: grey
      accent: indigo
      toggle:
        icon: material/weather-night
        name: Modo escuro
extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/Elvis-Almeida
    - icon: fontawesome/brands/linkedin
      link: https://www.linkedin.com/in/elvis-almeida/
```

### Estrutura Geral

**site_name:** Define o nome do site que será exibido no título e na navegação do site.

**nav:** Configura a navegação do site, especificando a estrutura do menu.

**theme:** Configura o tema do site, incluindo cores, logotipos e outros ajustes visuais.

**extra:** Adiciona informações extras, como links para redes sociais.

### Detalhamento das Configurações

Para personalizar a barra de navegação você pode criar da seguinte forma dento de `nav` sendo:

```yml
- Nome_da_opcao: Arquivo_que_contém_a_pagina_correspondete.md
```

E caso queira identar é só após o nome da opção colocar mais um "-" e o nome da opção novente com seu devido arquivo como abaixo:

```yml
- GLPI:
    - Instalando: glpi/instalando.md
```

Para personalizar o tema vamos configurar tudo em `theme`

```yml
theme:
  name: material # Aqui é definido o tema
  language: pt-BR # Aqui é definido a língua da página
  custom_dir: overrides # Aqui especifica um diretório de customizações para o tema.
  logo: logo.png # Aqui define a logo do site
  favicon: logo.png # Aqui define o icone do site
  palette: # Aqui configura esquemas de cores para o site.
    - media: "(prefers-color-scheme: light)" # Aqui é a configuração para o modo claro.
      scheme: default # Aqui define o esquema de cor padrão
      primary: grey # Aqui define a cor primária como cinza
      accent: indigo # Aqui define a cor de destaque
      toggle: # Aqui configura o botão de alternância entre modos claro e escuro
        icon: material/lightbulb # Aqui define o icone para o modo claro
        name: Modo claro # Aqui define o nome para modo claro
    - media: "(prefers-color-scheme: dark)" # Essa parte seque a mesma lógica da media anterior porém para o tema escuro
      scheme: slate # Aqui define o esquema de cores para o modo escuro
      primary: grey
      accent: indigo
      toggle:
        icon: material/weather-night # Icone modo noturno
        name: Modo escuro
```

Aqui nessa parte do `extra` definimos informações extras no site, nesse caso essas informações são as que aparecem na parte inferior do site

```yml
extra:
  social: # Esta linha inicia uma lista de ícones sociais que serão exibidos na documentação, aqui podemos adicionar links para redes sociais ou outros sites relevantes, como perfis de GitHub, LinkedIn, etc
    - icon: fontawesome/brands/github # Define o icone
      link: https://github.com/Elvis-Almeida # Define o link que o icone terá
    - icon: fontawesome/brands/linkedin # Define o icone
      link: https://www.linkedin.com/in/elvis-almeida/ # Define o link que o icone terá
```

Como nessa configuração colocamos a propriedade `custom_dir` apontando para a pasta `overrides` teremos que criar essa pasta para ela funcionar corretamente.

Nessa pasta podemos sobreescrever qual quer parte do site que desejar para que ele fique da forma que deseja.

Para criar a pasta vamos digitar `mkdir overrides` na raiz da pasta `mkdocs` que foi criada.

![Criando pasta](/mkdocs/images/criandopastaoverrides.png)

Com isso configurado podemos rodar o comando `mkdocs serve -a 10.0.0.2:5500` novamente para vermos a prévia do site de como ficou.

![Mostrando site configurado](/mkdocs/images/siteconfigurado.png)

Podemos até testar como ficar no modo branco clicando no icone da lua.

![Mostrando site configurado branco](/mkdocs/images/siteconfiguradobranco.png)

## Personalizando site

Agora como quero trocar o nome que está no rodapé escrito `Made with Material for MkDocs` para outro mais personalizado utilizarei a pasta `overrides` que foi criada anteriormente e configurada para por os arquivos nessesários para isso.

Como quero trocar somente a informação da parte inferior do site, será preciso criar um arquivo chamado `footer.html` e esse arquivo precisa está dentro de uma pasta chamada `partials` que esta por fim estará dentro da pasta que configuramos em `custom_dir` que é a `overrides` no nosso caso.

Para ficar mais claro, a arvore dos arquivos é assim:

```bash
overrides/
└── partials
    └── footer.html
```

Para fazer isso vamos criar a pasta `partials` com o comando:

```bash
mkdir partials
```

E o arquivo com o comando (execute o comando dentro da pasta `partials`):

```bash
touch footer.html
```

Com isso copiei o código padrão do footer do tema mkdocs-material indo em seu repositório no github, você pode acessa-lo [aqui](https://github.com/squidfunk/mkdocs-material/blob/master/src/templates/partials/footer.html), e colando no meu arquivo que acabei de criar.

![colando código](/mkdocs/images/colandocodigo.png)

Agora aqui fiz uma pequena modificação na parte final do código adicionando:

```html
<div class="md-footer-meta md-typeset">
  <div class="md-footer-meta__inner md-grid">
    <div class="md-copyright">
      ©2024
      <a href="https://escolahacker.com.br/capturetheflag/ctf/" target="_blank"
        >Secret Flag</a
      >. Todos os direitos reservados.
    </div>
    {% if config.extra.social %} {% include "partials/social.html" %} {% endif
    %}
  </div>
</div>
```

No lugar desse código:

```html
<div class="md-footer-meta md-typeset">
  <div class="md-footer-meta__inner md-grid">
    {% include "partials/copyright.html" %}

    <!-- Social links -->
    {% if config.extra.social %} {% include "partials/social.html" %} {% endif
    %}
  </div>
</div>
```

Ficará assim no código:

![codigo sobreescrito](/mkdocs/images/codigosobreescrito.png)

Agora é só salvar e rodar o site em modo de teste novamente para vermos como ficou:

![Site com novo footer](/mkdocs/images/sitecomnovofooter.png)

## Adicionando logo

Podemos ver que até o momento a logo do site não está aparecendo, isso ocorreu por que na configuração adicionamos o parâmetro `logo: logo.png` que define que o arquivo `logo.png` será a logo do nosso site, mas como não adicionamos esse aquivo, o mkdocs não carrega nenhuma imagem para lá.

Sendo assim agora vamos adicionar nossa logo. Para isso basta colocarmos o arquivo `logo.png` dentro da pasta `docs` do nosso projeto.

![Adicionando logo](/mkdocs/images/addlogo.png)

Como na pasta `docs` para o MkDocs é onde contém todos os documentos, ele entende que para referências de arquivos de documentação essa pasta é a raiz, por isso passamos somente `logo.png` pois ele irá buscar a imagem na raiz da pasta `docs` (Isso serve para os dumentos que vamos inserir mais tarde). Dito isso vamos ver como ficou:

![Site com logo](/mkdocs/images/sitecomlogo.png)

## Adicionando documentos

Vemos que na parte de navegação do site aparace as opções que definimos nas configurações que foram:

```yml
nav:
  - Home: index.md
  - GLPI:
      - Instalando: glpi/instalando.md
      - Usando: glpi/usando.md
  - MkDocs:
      - Instalando: mkdocs/instalando.md
      - Usando: mkdocs/usando.md
```

Como dito anteriormente a pasta docs guarda todos os documentos do nosso site, e ele é a pasta raíz dos documentos, por isso devemos criar nossos arquivos dentro da pasta `glpi` e `mkdocs` que ficará dentro da pasta `docs` como referênciamos na configuração.

Como até agora não criamos os arquivos que citamos nas configurações e caso você foi um curioso explorador deve ter deparado com essa tela:

![Página não encontrada](/mkdocs/images/paginaNotfound.png)

Para resolvermos isso vamos criar nossos arquivos respectivamente em suas pastas, como o processo para cada arquivo é o mesmo irei documentar somente o primeiro sendo os mesmos passos para os próximos.

Vamos criar a pasta `mkdocs` dentro da pasta `docs` e em seguida o arquivo `instalando.md` com os comandos:

Dentro da pasta `docs`

```bash
mkdir glpi
```

Dentro da pasta `glpi`

```bash
touch instalando.md
```

Estrutura das pastas:

```bash
docs/
├── glpi
│   ├── instalando.md
│   └── usando.md
├── mkdocs
│   ├── instalando.md
│   └── usando.md
├── index.md
└── logo.png
```

Com isso feito agora vamos ver como ficou:

![documentos criados](/mkdocs/images/documentosCriados.png)

## Documentando

Podemos ver na imagem anterior vemos que está vazio, de fato, por que não adicionamos nada nos arquivos criados.

Agora vou mostrar algumas dicas do markdown para documentação.

### Titulos

Usamos o símbolo **#** para criar títulos e subtítulos. Quanto mais **#**, menor o título.

```
# Título de Nível 1
## Título de Nível 2
### Título de Nível 3
#### Título de Nível 4
##### Título de Nível 5
###### Título de Nível 6
```

# Título de Nível 1

## Título de Nível 2

### Título de Nível 3

#### Título de Nível 4

##### Título de Nível 5

###### Título de Nível 6

### Ênfase

Podemos usar os asteriscos \* ou underscores \_ para ênfase. Um para itálico e dois para negrito.

```
*Itálico* ou _Itálico_
**Negrito** ou __Negrito__
***Itálico e Negrito*** ou ___Itálico e Negrito___
```

_Itálico_ ou _Itálico_

**Negrito** ou **Negrito**

**_Itálico e Negrito_** ou **_Itálico e Negrito_**

### Lista

Pode-se usar -, \* ou + para criar listas não ordenadas.

```
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
* Item 3
* Item 4
```

- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2

* Item 3
* Item 4

### Links

Podemos usar colchetes [] para o texto do link e parênteses () para a URL, para criar um texto com link.

```
[Link para o Google](https://www.google.com)
[Link com título](https://www.google.com "Título do link")
```

[Link para o Google](https://www.google.com)

[Link com título](https://www.google.com "Título do link")

### Imagens

Eu uso a mesma sintaxe dos links para imagens, mas adiciono um ponto de exclamação ! no início.

```
![Texto alternativo](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTJ0Q60OICwGKUWN8dc7jl0KZcFuMdK25ygMQ&s)

![Imagem teste](/mkdocs/images/foradoar.png)
```

![Texto alternativo](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTJ0Q60OICwGKUWN8dc7jl0KZcFuMdK25ygMQ&s)

![Imagem teste](/mkdocs/images/foradoar.png)

Aqui tem um exemplo com link e outro usando uma imagem local, para o uso de imagems local seque a mesma lógica dos arquivos dos documentos, onde criei uma pasta dentro de `mkdocs` com o nome `images` e dentro desta coloquei todas as imagens usadas neste documento.

Estrutura dos arquivos

```bash
docs/
├── glpi
│   ├── images
│   │     └── image.png
│   ├── instalando.md
│   └── usando.md
├── mkdocs
│   ├── images
│   │     └── image.png
│   ├── instalando.md
│   └── usando.md
├── index.md
└── logo.png
```

### Blocos de código

Para incluir código em linha, basta usar crases simples `. Para blocos de código, uso três crases ``` antes e depois do código.

```
`código em linha`
```

`código em linha`

(Ignore os pontos, eles foram utilizados para que o texto permanecesse visível)

````
. ```
.  código em bloco
. ```
````

```
  código em bloco
```

Você pode especificar a liguagem dessa forma

````
. ```html
.  <a>Hello Word</a>
. ```
````

```html
<a>Hello Word</a>
```

### Citações

Pode se usar **_>_** para criar citações.

```
> Esta é uma citação.
>
> Continua a citação.
```

> Esta é uma citação.
>
> Continua a citação.

### Linhas Horizontais

Pode usar três ou mais traços ---, asteriscos \*\*\* ou underscores \_\_\_.

```
---
***
___
```

---

---

---

Com isso acredito que esteja apto a começar sua jornada documentando com Mkdocs, espero ter ajudado.
