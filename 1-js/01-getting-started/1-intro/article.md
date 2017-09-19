# Uma introdução a JavaScript

Vamos ver o que há de tão especial sobre JavaScript, o que podemos alcançar e que outras tecnologias interagem bem com ele.

## O que é JavaScript?

*JavaScript* foi inicialmente criado para *"manter páginas web vivas"*.

Os programas nesta linguagem são chamados *scripts*. Eles podem ser escritos diretamente no HTML e executar automaticamente quando a página carrega.

Scripts são disponibilizados e executados como texto puro. Eles não necessitam de uma preparação especial ou compilação para executar.

Neste aspecto, JavaScript é muito diferente de outra linguagem chamada [Java](https://pt.wikipedia.org/wiki/Java_(linguagem_de_programação)).

```smart header="Por que <u>Java</u>Script?"
Quando o JavaScript foi criado, ele tinha inicialmente outro nome: "LiveScript". Mas naquela época, a linguagem Java era bem popular, então decidiu-se que posicioná-lo como "irmão mais novo" do Java iria ajudar.

Mas conforme sua evolução, o JavaScript se tornou uma linguagem completamente independente, com sua própria especificação chamada [ECMAScript](https://pt.wikipedia.org/wiki/ECMAScript), e hoje não tem relação nenhuma com Java.
```

Atualmente, JavaScript pode ser executada não somente no navegador, mas também no servidor, ou na verdade em qualquer dispositivo onde exista um programa especial chamado de [interpretador JavaScript ou as vezes motor JavaScript](https://en.wikipedia.org/wiki/JavaScript_engine).

O navegador tem um interpretador embarcado, algumas vezes também chamado de "máquina virtual JavaScript".

Diferentes interpretadores tem diferentes "codinomes", por exemplo:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- no Chrome e Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- no Firefox.
- ...Existem outros codinomes como "Trident", "Chakra" para diferentes versões do IE, "ChakraCore" para o Microsoft Edge, "Nitro" e "SquirrelFish" para o Safari, etc.

É bom lembrar os termos acima, pois eles são usados em artigos de desenvolvimento na internet. Nós iremos utilizá-los também. Por exemplo, se "uma funcionalidade X é suportada pelo V8", então provavelmente irá funcionar no Chrome e no Ópera.

```smart header="Como os interpretadores funcionam?"

Interpretadores são complicados. Mas o básico é fácil.

1. O interpretador (embarcado se for um navegador) lê ("analisa") o script.
2. Então ele converte ("compila") o script para linguagem de máquina.
3. E então o código de máquina é executado, bem rapidamente.

O interpretador aplica otimizações em cada estágio do processo. Ele até observa o script compilado enquanto ele é executado, analisa os dados que passam por ele e aplica otimizações no código de máquina baseado neste conhecimento. No fim, os scripts são bastante rápidos.
```

## O que o JavaScript no navegador pode fazer?

O JavaScript moderno é uma programação de linguagem "segura". Ele não provê acesso baixo nível a memória ou ao CPU, pois foi inicilamente criado para navegadores que não necessitam disto.

As possibilidades dependem bastante do ambiente que executa o JavaScript. Por exemplo, [Node.JS](https://wikipedia.org/wiki/Node.js) suporta funções que permitem o JavaScript ler/escrever em arquivos arbitrários, executar requisições na rede, etc.

O JavaScript no navegador pode fazer tudo relacionado a manipulação da página web, interação com usuário e com o servidor web.

Por exemplo, o JavaScript no navegador é capaz de:
For instance, in-browser JavaScript is able to:

- Adicionar trechos HTML a página, alterar o conteúdo existente, modificar estilos.
- Reagir a ações do usuário, executar ao clicar do mouse, ou ao mover o ponteiro, ou ao apertar uma tecla.
- Enviar requisições na rede para servidores remotos, baixar e enviar arquivos (as tecnologias tão faladas [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) e [COMET](https://en.wikipedia.org/wiki/Comet_(programming))).
- Recuperar e definir cookies, fazer perguntas ao visitantes, apresentar mensagens.
- Lembrar dados do lado do client ("local storage").

## O que o JavaScript no navegador NÃO pode fazer?

As habilidades do JavaScript no navegador são limitadas para o bem da segurança do usuário. O objetivo é prevenir uma página web má intencionada de acessar informações privadas ou danificar os dados do usuário.

Os exemplos de tais restrições são:

- O JavaScript em uma página web não pode ler/escrever dados arbitrários no disco rígido, copiá-los ou executar programas. Ele não tem acesso direto às funções do SO.

    Navegadores modernos permitem-no trabalhar com arquivos, mas este acesso é limitado e disponibilizado apenas se o usuário fizer certas ações, como "arrastando" um arquivo para o uma janela do navegador, ou selecionando-o através de uma tag `<input>`.

    Existem maneiras de interagir com câmeras/microfones e outros dispositivos, mas eles exigem uma permissão explícita do usuário. Desta forma, uma página com JavaScript habilitado não pode sorrateiramente habilitar a webcam, observar os arredores e enviar dados para a [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).


- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must contain a special JavaScript code that handles data exchange.

    The limitation is again for user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's safety limitations.

![](limitations.png)

Such limits do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow installing plugin/extensions which may get extended permissions.

## What makes JavaScript unique?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things done simply.
+ Supported by all major browsers and enabled by default.
```

Combined, these three things exist only in JavaScript and no other browser technology.

That's what makes JavaScript unique. That's why it's the most widespread tool to create browser interfaces.

While planning to learn a new technology, it's beneficial to check its perspectives. So let's move on to the modern trends that include new languages and browser abilities.


## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and autoconverting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntax sugar" for JavaScript, it introduces shorter syntax, allowing to write more precise and clear code. Usually Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing", to simplify development and support of complex systems. It is developed by Microsoft.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps). It was initially offered by Google as a replacement for JavaScript, but as of now, browsers require it to be transpiled to JavaScript just like the ones above.

There are more. Of course even if we use one of those languages, we should also know JavaScript, to really understand what we're doing.

## Summary

- JavaScript was initially created as a browser-only language, but now it is used in many other environments as well.
- At this moment, JavaScript has a unique position as the most widely-adopted browser language with full integration with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
