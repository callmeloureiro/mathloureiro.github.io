---
layout: post
title: Decifrando o WooCommerce Parte 01
categories: WooCommerce
---

Olá senhoras e senhores, tudo certo? Bom, espero que estejam muito bem, no meu caso estou indo né... Passei um tempo sem postar por falta de tempo mesmo, mas o importante é que estou de volta!!!

Antes de começarmos, gostaria de agradecer pelos feedback que estou tendo a respeito do blog e pela "Saga WooCommerce", OBRIGADO!!! Gostaria de **ressaltar** que o feedback e opinão a respeito disso é importantíssimo, pois é com a opinião de vocês que iremos melhorar cada vez mais, pois este blog não é apenas meu, é de todos nós!!! 

Se você ainda não opinou, possui uma dúvida ou quer apenas falar comigo, não se hesite em me contactar nas redes sociais e/ou no próprio comentário aqui do blog, irei responde-los com o maior prazer!

Enfim, chega de blablabla e vamos lá!

>**LET'S GO GUYS!**

Na postagem anterior, [O que há por trás do WooCommerce](http://www.matheusloureiro.com.br/woocommerce-o-que-ha-por-tras-dele/) aprendemos como é a estrutura do WooCommerce (sim, se escreve desse jeito '-' (sim, eu não estava escrevendo assim (sim, irei escrever agora do jeito correto '-'))) e já temos uma noção de como é o funcionamento do mesmo... Calma senhores, estamos pertinho de começar a **DESENVOLVER UM TEMA ADAPTADO AO WOOCOMMERCE** (*olha aí rapaz '-'*).

Controle a euforia e aguarde mais um **POUCO**!!! hahahaha, eu sou mal :3, mas tem um motivo... O motivo é que precisamos saber aonde mexer.

Como sabemos, o WooCommerce disponibiliza a sobrescrita dos arquivos, podemos muito bem ir lá e sobrescrever o template do jeito que queremos, né não? A resposta poderia ser sim... A não ser que, se você abrir os arquivos de template do WooCommerce, você perceberá que ele é um tanto diferente... Quer ver? Saca só!

![WooCommerce Content Single](/img/woocommerce-content-single.png)
<small>Errr... O que ser isso?</small>

Calma jovem!!! Não se assuste. Na imagem anterior, segue um pedaço de código do template *content-single-product.php*, responsável por exibir a single do produto. Percebemos que existe diversos **do_action**, responsável por chamar alguma função ligada ao **hook**! Beleza, mas o que é hook?

## Hooks do WooCommerce

O WooCommerce trabalha bastante com uma coisa chamada hook, ou se preferir, ganchos. Esses hooks permite que você manipule o código sem editar aquivos do core.

Dentro do Scaffold do WooCommerce existe um diretório chamado includes, e dentro dele possui um arquivo chamado **wc-template-hooks.php**, lá esta declarado todos os hooks padrões do WooCommerce... Existe também um outro arquivo bastante útil no mesmo diretório - includes/ -, o **wc-template-functions.php**, que trabalha em conjunto com os hooks.

Para verificarmos qual a função que o hook X está chamando, bastamos verificar qual o hook da determinada action e procurarmos a função correspondente do hook... Entendeu? Hum... Saca só!

> Vamos supor que eu quero verificar qual a função está atribuida ao hook (woocommerce_before_single_product_summary) presente no arquivo **content-single-product.php**

{% highlight php %}
  <?php
    /**
     * woocommerce_before_single_product_summary hook
     *
     * @hooked woocommerce_show_product_sale_flash - 10
     * @hooked woocommerce_show_product_images - 20
     */
    do_action( 'woocommerce_before_single_product_summary' );
  ?>
{% endhighlight %}

![Hook](/img/hook.png)

Saporra é essa? '-'
<small><small>Sim jovem... São duas funções atribuídas a um hook! Hahahahahaha... Negócio é trilouco veei '-'</small></small>



Além disso existe uma "ordem" no hook, no nosso caso o hook **(woocommerce_before_single_product_summary)** possui a ordem 10 e 20 respectivamente as funções woocommerce_show_product_sale_flash e woocommerce_show_product_images, que quando feito a chamada do hook, as ordens irá servir na exibição (10 aparecerá primeiro que 20 '-').

Basicamente... O WooCommerce é feito assim, através de hooks! Na próxima postagem iremos fazermos as nossas funções para os hooks... Aguarde!

* Caso tenha alguma dúvida... Não se HESITE em falar, utilize o comentário abaixo ou me chame nas redes sociais!!! 

Fui!

