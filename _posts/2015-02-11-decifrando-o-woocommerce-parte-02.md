---
layout: post
title: Decifrando o WooCommerce Parte 02
categories: WooCommerce
---


Senhoras e senhores... Depois de um tempo sem postar, estamos novamente continuando o show! Estava realmente sem tempo e gostaria de agradece-los pela cobrança que tive para fazer uma nova matéria :), isso foi fantástico!

Continuando o show... Vamos prosseguir a postagem anterior, caso você não tenha visto ainda, [Clique aqui](http://www.matheusloureiro.com.br/decifrando-o-woocommerce-parte-01/) e sinta o poder que você já poderá conseguir fazer :).

>**LET'S GO GUYS!**

Já sabemos como o WooCommerce funciona, então vamos listar agora o que já vimos aqui...
* Scaffold do WooCommerce
* Sobreposição dos arquivos templates do WooCommerce
* Funcionamento de um hook

<small>Caso você tenha perdido alguma dessas matérias, [entre aqui](http://www.matheusloureiro.com.br/categorias/woocommerce/) e veja todo o material relacionado a WooCommerce.</small>

Então... Estamos próximos a começar a desenvolver de fato, mas antes, irei listar algumas coisas que costumo utilizar e porque deles existirem no meu projeto.

* [Foundation](http://foundation.zurb.com)
  * Framework CSS, foudation tornou-se uma mão na roda no desenvolvimento, ajudando na agilidade do meu projeto como também na qualidade dele. Normalmente vocês devem utilizar o [Bootstrap](http://getbootstrap.com/), mas eu particulamente não gosto, achei o foundation bem mais inteligente do que o Bootstrap principalmente quando usado algum **Pré-processador**...
* [SASS](http://sass-lang.com)
  - Sass pré-processador, antes de escolher qual pre processador utilizar, testei um por um e me simpatizei muito com o sass... E quando percebo, lá na doc do **FOUNDATION** percebemos também que eles utilizam o sass '-', isso foi muito da hora! [LESS](http://lesscss.org) também é muito da hora, mas... Confiram essa tabela e tirem suas conclusões: [Sass x Less](http://www.hongkiat.com/blog/sass-vs-less/)
* [Gulp](http://gulpjs.com)
  - Gulp automatizador, com o mesmo propópsito do [Grunt](http://gruntjs.com), o Gulp veio para agilizar mais ainda o trabalho que o Grunt fazia, sendo o Gulp mais rápido na execução de tarefas... Diferentemente do Grunt, você escreve tarefas do Gulp em JavaScript(algo parecido com o nodeJS) e não em JSON usado no Grunt. O diferencial realmente está no quesito de velocidade que no resultado final dá uma grande diferença.
* [Roots.io](http://roots.io/)
  - Roots starter theme wordpress, para quem não conhece o Roots, ele é um starter theme para wordpress, ou seja, um tema já pronto para você começar a desenvolver. Ele é um projeto muito show, tem alguns diferenciais bacanas como o Wrapper. Pra galera que conhece o Laravel, o wrapper funciona como o @extends, onde há uma base e você irá escrever apenas entre o body, preservando assim o header e o footer sem a necessidade de ficar dando include :). Porém ele default tras consigo o bootstrap e grunt, maaaas, como eu não curto tanto eles, então tive a necessidade de criar um a meu gosto né? '-', Apresento-lhes o [LOUME](https://github.com/mathloureiro/Loume), baseado no [GROMF](https://github.com/cicerohen/gromf), um tema baseado no Roots.io porém utilizando gulp, foundation e sass '-', da hora né?

> Então é isso, agora vamos colocar mão na massa!

O que basicamente precisamos saber nós já sabemos então não há nada que nós impeça de desenvolver um tema agora de fato, então na sua function.php iremos começar a brincar '-'.

Como falado ao decorrer dessa série, os hooks são responsáveis por atribuir a função no seu projeto, logo leva a crer que além do hook existe uma função atrelada e ele. Há três formas de manipularmos os hooks

* Adicionando add_action();
* Removendo remove_action();
* Filtrando add_filter();

add_action, usado para adicionar uma função a um hook. <br>
remove_action, usado para remover uma função de um hook. <br>
add_filter, usado para sobrescrever certas funções. <br>

Vamos supor que eu quero remover a sidebar do WooCommeerce, então já sabemos o que utilizar... Concordam comigo que é a remove_action()? 

Ok, é ela '-'.

{% highlight php %}
  add_action( 'woocommerce_sidebar', 'woocommerce_get_sidebar', 10)
{% endhighlight %}

Esse é o hook responsável por chamar a sidebar no nosso site... Se lermos ele um pouco, veremos que existe uma função chamada woocommerce_get_sidebar, com o nome do hook denominado por woocommerce_sidebar e que tem a posição ou ordem 10. Bastamos trocar o add_action por remove_action, ficando assim:

{% highlight php %}
remove_action( 'woocommerce_sidebar', 'woocommerce_get_sidebar', 10).
{% endhighlight %}

Beleza, conseguimos remover a sidebar :).

Vamos supor que eu quero adicionar uma sidebar criada por mim no lugar da sidebar original do WooCommerce. 

Então, depois de removida, temos esse espaço do hook disponível para colocarmos o que quisermos, então bastamos escrever isso aqui: 

{% highlight php %}
add_action( 'woocommerce_sidebar', 'SUA_FUNCAO', 10);
{% endhighlight %}

Será substituida pela a sua função :).

Para finalizar, vamos supor que eu quero mudar o nome que aparece na tab descrição do produto... Quero colocar o nome do produto como título.

Como já existe uma função responsável pra isso, então podemos sobrescreve-la pela nossa... Ficando assim:

{% highlight php %}
  add_filter( 'woocommerce_product_tabs', 'loureiro_mudaNome_titulo_tabs', 10, 1 );
{% endhighlight %}

{% highlight php %}
  function loureiro_mudaNome_titulo_tabs( $tabs ) {
    global $post;
    if ( isset( $tabs['description']['title'] ) )
      $tabs['description']['title'] = $post->post_title;
    return $tabs;
  }
{% endhighlight %}

Voy lá! Conseguimos mudar o nome da tab :).

Então por hoje é só galera! Espero que tenham gostado, até a próxima!