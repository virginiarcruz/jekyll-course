# Reestruturando o tema

* Limpar o aquivo index.html e o default.html
* Fazer um html estático para o default.

## Utilizando variáveis dinâmicas para as páginas

* Tenho que usar o escopo site.
    ```
    site.title
    ```

* Os títulos deve ser um para cada página, então vou fazer uma condicional para o title do site
    
    ```bash
    <title>{% if page.title %} {{page.title}} {% else %} {{ site.title }} {% endif %}</title>
    ```

* Para o conteúdo basta incluir a tag
    `` {{ content }} ``

* Para incluir links das páginas na home.
    - Se eu colocar `` site.pages `` o jekkyl vai me entregar uma lista com todas as pages criadas.

    ```bash
    <nav class="masterhead-nav">
      {% for page in site.pages %}
        <a href="{{ page.url }}">{{ page.title }}</a>
      {% endfor %}
    </nav>
    ```
    

## Layout com listagem dos posts

* Vamos listar o title e a page do post.
    - primeiro preciso iterar post a post, então no index vou fazer um for de todos os posts, assim como da url e da data.

    ```bash
    {% for post in site.posts %}
        <div class="content list">
            <div class="list-item">
                <h2 class="list-post-title">
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
                <div class="list-post-date">
                    <time>{{ post.date }}</time>
                </div>
            </div>
        </div>
    {% endfor %}
    ```

* Para o post pegar a baseurl
    - filter - recebe um dado e faz um tratamento do outro lado.
    - Para adicionar a baseurl antes do link da pagina uso o preprend

        `` "{{ post.url | prepend: site.baseurl }} ``

    - Para a data, uso um filtro que formata a data de forma mais legível

        `` {{ post.date | date_to_string }}``

* Para o caso de não ter nenhum post, vamos fazer uma condicional

    ```bash
    {% if site.posts.size == 0 %}
        <h2>No posts found</h2>
    {% else %}
        {% for post in site.posts %}
         #conteudo do for para os posts
        {% endfor %}
    {% endif %}
    ```

## Criando uma página

- Para adicionar uma página ao site, crio a page na raiz, por exemplo: ``contact.md`` e adiciono a ela o titulo necessário, dizendo qual layout ela vai ter e etc

        ---
        layout: page
        title: Contact Us
        permalink: /contact/
        ---
    
    Dentro da page posso adicionar conteúdo por markdown em html

    - No caso que tratamos a página contato tem o layout da page


- Página de post
