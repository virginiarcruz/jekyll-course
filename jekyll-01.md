# Criar site estático usando jekyll

* Simplicidade - reaproveitamento de código (template unico)
* Não possui banco de dados
* Qualquer servidor suporta
* Markdown para escrita
* Sistemas de templates com condicionais e filtros.

## Instalar o Jekyll

* [Instalar Ruby](https://www.ruby-lang.org/en/documentation/installation/)
* [Jekyll Windows](http://jekyll-windows.juthilo.com)
* [Documentação Jekyll](https://jekyllrb.com/docs/installation/)



## Utilizando o Jekyll

* [Imports para Jekyll](http://import.jekyllrb.com)
* Para iniciar o blog

    ```jekyll new minimal-blog```

* Os temas do jekyll são separados em bases. Não vem com pastas layouts, includes etc.
* Com o comando ``bundle show minima``, vejo onde está a estrutura do minima
    * Terei o local onde está o template minima e posso listar os arquivos do template
    * Dentro do arquivo **config.yml** que está na pasta do meu blog, ele manda carregar os arquivos do template.
    * Como no caso em que trabalhamos queremos copiar toda a estrutura, vamos executar o comando para abrir a pasta e copiar e colar toda a estrutura para o **minimal-blog**

* No terminal volto para a pasta do minimal-blog e executo:

      bundle exec jekyll build
    
    Para ver o site rodando

      bundle exec jekyll s


## Configurando o blog

* A Primeira coisa que será necessário fazer é configurar o arquvivo **config.yml**
    * no início de tudo iremos editar as configurações deste arquivos e não precisaremos mais mexer.

* Para configurar a url dos posts:

      permalink: /:year/:month/:day/:title


## Estrutura do Jekyll

* Front Matter - definição estrutural onde posso definir informações atraves de atribuição de chave e valor
* Liquid template - é o que permite fazer includes dentro do HTML

    ```bash
    ---
    layout: default
    ---
    # Quer dizer que vou na pasta Layout/default

    {%- include header.html -%}
    # indica que eu vou passar um comando dentro do espaço. Vou incluir dentro desse espaço tudo o que tiver no header.

    # O arquivo include sõ incluir o que estiver dentro da pasta _includes

    ```
    
* Para adicionar uma variável com o Liquid Template

    ```js
    --- 
    layout: default
    message: "teste liquid"
    ---

    <h1>{{ page.message }}</h1>

    ```
    * na estrutura atual do jekyll ele carrega o arquivo index.md, usando o layout da home. Então até este ponto do curso substituí o index.md por index.html utilizando o template default e assim ele aceita a chamada de variáveis dentro do arquivo.


* Posso fazer um for dentro do template da seguinte forma:

    - chamo as tags no início
    ```js
        tags:
        - jekyll
        - blog
        - minimalista
    ```
    - Faço o for para passar por cada uma das tags
    ```bash
    {% for tag in page.tags %}
        <h2> {{ tag }} </h2>
    {% endfor %}
    ```


## Condicionais no Liquid Template

- Posso fazer condicionais no template
    - Seto a variável no topo

          show_footer: false
    
    - E no bloco que quero fazer a condicional eu faço o if se ela deve aparecer ou não.

        ```bash
        {% if page.show_footer %}
        <footer>
            <p>By Virginia </p>
        </footer>
        {% endif %}
        ```

