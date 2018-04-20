# Implementando um sistema de comentários


- Adicionar comentários do [Disqus](disqus.com) na página.
    - acessar página do discus.
    - Seguir os passos básicos para adicionar no site
    - Para configurar as variáveis

    ```js
     var disqus_config = function () {
      this.page.url = '{{ site.url }}{{ site.baseurl }}{{ page.url }}';  /* dominio / baseurl / urldopost;  */
      this.page.identifier = '{{ page.url}}'; 
      };
    ```
- Seguir as configurações do site.


# Funcionalidade de Tempo de leitura

- Criar um arquivo no includes `minutes to read`
- A cada 1 minuto uma pessoa lê 180 palavras, 2 minutos 360 e assim por diante.

    ```js
    //Para descobrir quantas palavras o post possui
    {% assign words = content | number_of_words %}
    ```

    - `assing` - para criar uma variável na condicional
    - Então adiciono o include que criei na página de posts
        
          {% include minutes-to-read.html %}


    ```bash
        #código para a lógica da leitura
        {% if words < 360 %}
            #crio a variável minutesText e digo que se ela for menor que 360 vou ler em  minuto
            {% assign minutesText = '1 minute to read' %}
        {% else %}
            # se não for menor que 360, divido o numero de palavras por 180 e ao final adiciono o texto minutes to read
            {% assign minutesText = words | divided_by:180 | append: ' minutes to read' %}
        {% endif%}
    ```

    - no página de post adiciono na tag que criei para exibir o tempo de leitura
         
          <span class="reading-time">{{minutesText}}</span>



## Criar novos posts

- Só criar um novo arquivo com a nomenclatura do post já existente e editar o topo.
- As pages utilizam [markdown](https://daringfireball.net/projects/markdown/basics)


## Limpar os arquivos do jekyll

- Limpar os arquivos do tema, fazer os includes corretamente do header, head, footer e etc.


# Publicar o site

- [Git Hub Pages](https://pages.github.com)
- Utilizar o githubpages para publicar o site.

- A branch gh-pages - vai ficar tudo que iremos ter na página

        git checkout -b gh-pages
        git push origin pages

    - vai subir os arquivos da master para gh-pages

- [Post do Willian](https://willianjusten.com.br/dominio-proprio-no-github-pages/) sobre o Github Pages