---
layout: post
title: Woocommerce, o que há por trás dele?
categories: WooCommerce
---

Olha eu novamente galera '-', antes de começar o post gostaria de agradecer a todos aqueles que deram seu feedback referente a primeira postagem, percebi que houve uma aceitação muito boa e eu gostaria agradecê-los por isso!
> **OBRIGADOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO**
> **PESSOALLLLLLLLLLLLLLLL VOCÊS SÃO F0D4S PRA C4R4LH0...**

{% highlight bash %}
    01101111 01100010 01110010 01101001 01100111 01100001 
    01100100 01101111 00100000 01100101 01101101 00100000 
    01101101 01101111 01100100 01101111 
    00100000 01101110 01100101 01110010 01100100 00100001 
{% endhighlight %}

{% highlight bash %}
    $ echo "entendedores entenderão '-'"
{% endhighlight %}

Então é isso... chega de agradecimento e vamos para o que interessa <big>##WOOCOMMERCE##<big>!

>**LET'S GO GUYS!**

Na postagem anterior, onde começamos o [Getting Started Woocommerce](http://www.matheusloureiro.com.br/getting-started-woocommerce/), aprendemos o introdutório mesmo do que é o **woocommerce** e como instalar no nosso wordpress, porém, foi algo muito simples, que tal nos aprofundarmos um pouco no assunto?

O Woocommerce traz consigo um layout já pronto, quando você acessa qualquer página que o woocommerce gerou, percebe-se de que há alguma coisa dentro delas. Você deve está se perguntando... Matheus, é só editar o CSS? Eu te respondo... Jovem, é uma alternativa, mas cá entre nós, nem eu nem você queremos ficar apenas nisso; Eu quero conseguir fazer o negócio do '0' e você?

A estrutura do WooCommerce é assim oh:

    - woocommerce/
        assets/
        dummy-data/
        i18n/
        includes/
        templates/
        licence.txt
        readme.txt
        uninstall.php
        woocommerce.php


*Obs: Esse Scaffold está dentro da pasta plugins/*

PESSOALLLLLLLLL!!! Lembra que eu falei que o woocommerce vinha com um layout já pronto? Advinha onde está esse layout? '-' 
Tá... vou falar, ele está dentro da pasta **templates/**

    - woocommerce/
        templates/
            cart/
            checkout/
            emails/
            global/
            loop/
            myaccount/
            notices/
            order/

Dentro da pasta templates, existe o layout padrão do woocommerce... <br>


- cart/carty-empty.php > Ele é responsável pelo template que há no carrinho de compras quando está vazio (cart/ diretório onde há templates de carrinho);
![Cart](/img/cart.png)

- checkout/form-checkout.php > Responsável pelo template do formulário de checkout (checkout/ diretório onde há templates de checkout);
![Checkout](/img/form-checkout.png)

* global/breadcrumb.php > Responsável pelo template do breadcrumb (global/ refere-se ao diretório que contém templates comuns a várias áreas);

* loop/add-to-cart.php > Responável pelo template do botão que adiciona ao carrinho (loop/ diretório onde há templates de loop);

* myaccount/my-account.php > Responsável pelo template da minha conta (myaccount);
![Account](/img/account.png)

* notices/ > Diretório onde há templates de notícias do woocommerce;
![Notices](/img/notices.png)

* order/order-details.php > Responsável pelo template dos Meus Pedidos (order/ diretório onde há templates de pedidos).

Bom... Agora sabemos o Scaffold do Woocommerce, mas calma, ainda não acabou! hahahahahaha (falei que esse post seria mais completo!)

Você deve está se perguntando... Matheus, agora eu já sei onde editar meu template, posso começar a editar? Eu te digo jovem, começar a editar, AI **NÃO**! Mas porque? Imagine que o plugin sofre uma atualização e ele precisa atualizar os arquivos default do woocommerce, então, podemos perder todo o trabalho que tivemos... Pensando nisso, a galera do WooCommerce disponibilizou a sobrescrita desses arquivos.

>Sobrescrita do Woocommerce

Para sobrescrevermos esses arquivos, precisamos criar uma pasta chamada **woocommerce** dentro do nosso tema do wordpress, em seguida, dizermos qual o arquivo iremos sobrescrever... Exemplo:

**Eu quero sobrecrever o template cart/carty-empty.php responsável pelo carrinho vazio, como devo proceder ?**

Jovem, dentro do seu tema do wordpress, você irá criar uma pasta chamada woocommerce, como dito anteriormente, porém o arquivo carty-empty.php está dentro da pasta cart/, logo, o que devemos fazer? Criar uma pasta chamada cart dentro da pasta woocommerce, ficando assim oh:
    
    - wp-content
        themes/
            seu_tema/
                woocommerce/
                    cart/
                        carty-empty.php

E então só copiar o que está dentro de *plugins/woocommerce/cart/carty-empty.php* para o seu arquivo carty-empty.php que está dentro do seu tema, e fazer as devidas alterações. Assim evitamos de que uma atualização nos traga uma dor de cabeça!

Por hoje é só... Agradeço a atenção e bons estudos!



