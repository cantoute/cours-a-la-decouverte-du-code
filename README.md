# À la découverte du code

## Vos bibles

- https://developer.mozilla.org/fr/docs/Web/Tutorials
- https://www.alsacreations.com/
- https://htmlcheatsheet.com/
- https://stackoverflow.com/

### Utils

- Prettier

---

## HTML

### Structure d'un document html minimal

```html
<!DOCTYPE html> <!-- cette ligne déclare le document html5 -->
<html>
  <head>
    <title>Titre de page</title>
  </head>
  <body>
    ...
  </body>
</html>
```

### Les "bonnes pratiques"
```html
<!DOCTYPE html>
<html lang="fr-FR">
  <head>
    <title>Titre de page</title>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8" />
    <meta
      id="viewport"
      name="viewport"
      content="width=device-width, initial-scale=1"
    />
    <meta name="robots" content="index, follow" />
    <meta
      name="robots"
      content="max-snippet:-1, max-image-preview:large, max-video-preview:-1"
    />

    <!-- Styles -->
    <link href="style.css" type="text/css" rel="stylesheet" media="all" />

    <style>
      /* styles spécifiques à la page */
    </style>

    <!-- Icon -->
    <link rel="shortcut icon" type="image/ico" href="favicon.ico" />
    <!--
      <link rel="apple-touch-icon" href="apple-touch-icon.png" />
      <link
        rel="apple-touch-icon"
        sizes="72x72"
        href="apple-touch-icon-ipad.png"
      />
      <link
        rel="apple-touch-icon"
        sizes="114x114"
        href="apple-touch-icon-iphone4.png"
      />
    -->

    <meta property="og:title" content="Cours initiation au code" />
    <meta property="og:description" content="HTML CSS JavaScript" />
    <meta property="og:site_name" content="exemple.com" />
    <meta property="og:type" content="article" />
    <meta property="og:locale" content="fr_FR" />
    <meta
      property="og:image"
      content="https://www.exemple.com/img/illustration.jpg"
    />
  </head>
  <body>
    [...]
  </body>
  <!-- Scripts -->
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="script.js"></script>
  <script>
    'use strict';

    var str = 'Hello world!';

    console.log(str);
    // Hello world!
  </script>
</html>
```

### Les liens

```html
<!--
  ###################
  # Chemins absolus #
  ###################
-->
<a href="https://exemple.com/">Exemple</a>
<a href="//exemple.com/">Exemple transport indépendant</a>

<a href="/a-propos">Se dit absolut aussi... Mais plus précisément il est relatif à la racine du site.</a>

<!--
  ####################
  # Chemins relatifs #
  ####################
-->
<a href="chapitre-1">Chapitre 1</a>
<!-- équivalent à -->
<a href="./chapitre-1">Chapitre 1</a>

<!-- remonter dans la hiérarchie -->
<a href="../cours-2">Cours 2</a>

<!--
  ##########
  # Target #
  ##########
-->
<!-- Nouvel onglet -->
<a href="../cours-2" target="_blank">Cours 2</a>

<!-- comportement par défaut -->
<a href="../cours-2" target="_self">Cours 2</a>

<!-- dans le cas d'utilisation de frame/iframe (frame = mauvaises pratiques) -->
<a href="../cours-2" target="_parent">Cours 2</a>

```

### Les attributs

```html
<!-- les attributs globaux -->
<span
  class="pink-floyd star music"
  id="pink-floyd"
  style="text-decoration: underline; font-wight: bold;"
  onclick="return false;"
  title="Info bulle"
  >Pink Floyd</span>
```
Lire + https://developer.mozilla.org/fr/docs/Web/HTML/Global_attributes

---

## CSS

### Eléments type block

```html
<!-- les espaces avant/après (leading/trailing) sont ignorés -->
<div /> <h1 /> <section /> <article /> <nav /> <pre /> <hr />
```

### Eléments type inline

```html
<!-- les espaces avant/après (leading/trailing) sont respectés -->
<span /> <a /> <i /> <strong /> <img />

<a href="#">
  ceci est un lien
</a>
<!-- cela joue surtout un rôle pour le (dé)calage des images -->
<a href="#">ceci est un lien</a>
<a href="#"
  >Voici l'astuce</a>
```

### Sélecteurs

```css
*       /* all elements */
div     /* all div tags */
div,p   /* all divs and paragraphs */
div p   /* paragraphs inside divs */
div > p /* all p tags, one level deep in div */
div + p /* p tags immediately after div */
div ~ p /* p tags preceded by div */
.classname /* all elements with class */
#idnameelement  /* with ID */
div.classname   /* divs with certain classname */
div#idname      /* div with certain ID */
#idname *       /* all elements inside #idname */


/****************
 * Pseudo classes
 ****************/
a:link    /* link in normal state */
a:active  /* link in clicked state */
a:hover   /* link with mouse over it */
a:visited /* visited link */
p::after{content:"yo";} /* add content after p */
p::before /* add content before p */
input:checked /* checked inputs */
/* ... */

/*********************
 * Attribute selectors
 *********************/
a[target]         /* links with a target attribute */
a[target="_blank"]/* links which open in new tab */
[title~="chair"]  /* title element containing a word */
[class^="chair"]  /* class starts with chair */
[class|="chair"]  /* class starts with the chair word */
[class*="chair"]  /* class contains chair */
[class$="chair"]  /* class ends with chair */
input[type="button"] /* specified input type */
```

Lire + https://htmlcheatsheet.com/css/

---

## DOM

<cite>
Le Document Object Model (DOM) est une interface de programmation normalisée par le W3C, qui permet à des scripts d'examiner et de modifier le contenu du navigateur web1. Par le DOM, la composition d'un document HTML ou XML est représentée sous forme d'un jeu d'objets – lesquels peuvent représenter une fenêtre, une phrase ou un style, par exemple – reliés selon une structure en arbre1. À l'aide du DOM, un script peut modifier le document présent dans le navigateur en ajoutant ou en supprimant des nœuds de l'arbre1.
<cite>

https://fr.wikipedia.org/wiki/Document_Object_Model

<br>

<p>
<img src="./assets/img/dom.png">
</p>

---

## JavaScript

### Vanilla

```js
document.addEventListener("DOMContentLoaded", function(event) {
    // Your code to run since DOM is loaded and ready
});

var msg = 'OK!'
/*
msg = 'Astuce pour commenter une section';
// */

console.log(msg)
// OK!
```

### jQuery

<cite>
jQuery est une bibliothèque JavaScript libre et multiplateforme créée pour faciliter l'écriture de scripts côté client dans le code HTML des pages web3. La première version est lancée en janvier 2006 par John Resig.

Le but de la bibliothèque étant le parcours et la modification du DOM (y compris le support des sélecteurs CSS 1 à 3 et un support basique de XPath), elle contient de nombreuses fonctionnalités ; notamment des animations, la manipulation des feuilles de style en cascade (accessibilité des classes et attributs), la gestion des évènements, etc. L'utilisation d'Ajax est facilitée et de nombreux plugins sont présents.

Depuis sa création en 2006 et notamment à cause de la complexification croissante des interfaces Web, jQuery a connu un large succès auprès des développeurs Web et son apprentissage est aujourd'hui un des fondamentaux de la formation aux technologies du Web. Il est à l'heure actuelle la bibliothèque front-end la plus utilisée au monde (plus de la moitié des sites Internet en ligne intègrent jQuery).

Cependant, son utilisation devient moins pertinente avec l'émergence de nouvelles bibliothèques telles que React (JavaScript) et Vue.js qui la remplacent dans la construction d'Application web monopage.
</cite>
https://fr.wikipedia.org/wiki/JQuery


```js
'use strict';

$(document).ready(function() {

});

/*********************************
 * Mode compatibility (Wordpress)
 * jQuery() est l'équivalent de $()
 *********************************/

(function ($) {
  // here you can call jQuery via $
  // and your variables are isolated
  $(function() {
    // this is a shortcut to $(document).ready()
    // and will be executed when DOM is ready
  })
})(jQuery);

```

### Expression régulières (RegExp)

**Le super "Rechercher/Remplacer" hérité du langage PERL**

N'aura rien de régulier à votre sens, mais un incontournable !

## Format des images

### sans perte de qualité (lossless)
#### gif
la blague !!

#### png

### avec perte de qualité (lossy)
#### jpeg

### Bi
#### webp

### Vectoriel
#### svg

## Serveur web

### Apache

.htaccess

```apache
# Redirect status 302
Redirect temp /short-url /some/long/url
# ! Note !
# redirigera /short-url/more?query=1234
# en /some/long/url/more?query=1234

# il est préférable de tester une redirection
# en status 302 (temporaire) avant de la déclarer
# en mode permanent (301)
Redirect permanent /old-url /new-url
```

### http headers

```bash
$ curl -I https://httpd.apache.org/
HTTP/1.1 200 OK
Date: Fri, 21 May 2021 03:19:10 GMT
Server: Apache
Last-Modified: Thu, 22 Apr 2021 10:57:01 GMT
ETag: "25c5-5c08d89f6ae7c"
Accept-Ranges: bytes
Content-Length: 9669
Vary: Accept-Encoding
Content-Type: text/html

#######################

$ curl -I https://www.google.com/
HTTP/2 200 
content-type: text/html; charset=ISO-8859-1
p3p: CP="This is not a P3P policy! See g.co/p3phelp for more info."
date: Fri, 21 May 2021 03:17:27 GMT
server: gws
x-xss-protection: 0
x-frame-options: SAMEORIGIN
expires: Fri, 21 May 2021 03:17:27 GMT
cache-control: private
set-cookie: 1P_JAR=2021-05-21-03; expires=Sun, 20-Jun-2021 03:17:27 GMT; path=/; domain=.google.com; Secure
set-cookie: NID=216=L2Iw8nlcBDbqW5tw7fEDYyuazH-MnAqUyjfjRod2-5WMhWevc9en0-l-NILgxY2trtQzR4RCPjftASt5LKs2g44Fkin5o0B1bJW_0KgBm9F--o22o2TsKtiPkidhpwhmRKPyPTcv1_xo70SSbEWf4-4Rw0R3BkHl-4FUffYrh1s; expires=Sat, 20-Nov-2021 03:17:27 GMT; path=/; domain=.google.com; HttpOnly
alt-svc: h3-29=":443"; ma=2592000,h3-T051=":443"; ma=2592000,h3-Q050=":443"; ma=2592000,h3-Q046=":443"; ma=2592000,h3-Q043=":443"; ma=2592000,quic=":443"; ma=2592000; v="46,43"

```
