# À la découverte du code

## Vos bibles

- https://developer.mozilla.org/fr/docs/Web/Tutorials
- https://www.alsacreations.com/
- https://htmlcheatsheet.com/
- https://stackoverflow.com/
- [css-cheat-sheet.pdf](assets/css-cheat-sheet.pdf)
- https://openclassrooms.com/fr/

### Utils

- Prettier
- 7-zip
- https://jsfiddle.net/

---

## HTML

### Structure d'un document html minimal

```html
<!DOCTYPE html>
<!-- cette ligne déclare le document html5 -->
<html>
  <head>
    <title>Titre de page</title>

    <meta charset="UTF-8" />

    <!-- sans lui, pas de Responsive -->
    <meta name="viewport" content="width=device-width, initial-scale=1" />
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

    <meta charset="UTF-8" />

    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <!-- <meta name="viewport" content="initial-scale=1, maximum-scale=1"> -->

    <!-- SEO -->
    <meta name="robots" content="index, follow" />
    <meta
      name="robots"
      content="max-snippet:-1, max-image-preview:large, max-video-preview:-1"
    />

    <meta
      name="description"
      content="Ceci permet de forcer les 3 lignes sous le lien de google. De façon générale il est préférable de ne pas le définir et ainsi laisser les moteurs de recherches fournir un texte automatique basé sur les mots de la recherche. Toutefois, pour une page d'accueil, une tête de section ou une page contenant peut de texte ou encore si le texte retenu par les moteurs de recherche est peut approprié, il est alors préférable de le renseigner."
    />

    <!-- Sera surtout utile pour se positionner sur des fautes de frappes courantes -->
    <meta name="keywords" content="initiation code html css js" />

    <!-- Styles -->
    <link
      href="assets/style.css"
      type="text/css"
      rel="stylesheet"
      media="all"
    />

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

    <!-- Facebook -->
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
  <script src="assets/script.js"></script>
  <script>
    // forcer l'utilisation de déclarations des variables.
    "use strict";

    var str = "Hello world!";

    console.log(str);
    // Hello world!
  </script>
</html>
```

### Les liens

```html
<!--
  ##################################
  # Chemins absolus - Absolut path #
  ##################################
-->
<a href="https://exemple.com/">Exemple</a>
<a href="//exemple.com/">Exemple transport indépendant</a>

<a href="/a-propos"
  >Se dit absolut aussi... Mais plus précisément il est relatif à la racine du
  site.</a
>

<!--
  ####################################
  # Chemins relatifs - Relative path #
  ####################################
-->
<a href="chapitre-1">Chapitre 1</a>
<!-- équivalent à -->
<a href="./chapitre-1">Chapitre 1</a>

<!-- remonter dans la hiérarchie -->
<a href="/tmp/cours-2">Cours 2</a>

<!--
  ##########
  # Target #
  ##########
-->
<!-- Nouvel onglet -->
<a href="/tmp/cours-2" target="_blank">Cours 2</a>

<!-- comportement par défaut -->
<a href="/tmp/cours-2" target="_self">Cours 2</a>

<!-- dans le cas d'utilisation de frame/iframe (frame = mauvaises pratiques) -->
<a href="/tmp/cours-2" target="_parent">Cours 2</a>
```

<img src="assets/img/URI_syntax_diagram.svg" style="background-color: silver; padding:1em;" />

```js
function parseUrl(url) {
  /*
   * https://tools.ietf.org/html/rfc3986#appendix-B
   * ^(([^:/?#]+):)?(//([^/?#]*))?([^?#]*)(\?([^#]*))?(#(.*))?
   *  12            3  4          5       6  7        8 9
   *
   * Ex: http://www.ics.uci.edu/pub/ietf/uri/#Related
   *
   * $1 = http:
   * $2 = http                  // Scheme
   * $3 = //www.ics.uci.edu
   * $4 = www.ics.uci.edu       // Host
   * $5 = /pub/ietf/uri/        // Path
   * $6 = <undefined>
   * $7 = <undefined>           // Query String
   * $8 = #Related
   * $9 = Related               // fragment
   */
  const urlParse =
    /^(([^:\/?#]+):)?(\/\/([^\/?#]*))?([^?#]*)(\?([^#]*))?(#(.*))?/;

  return url.match(urlParse) || null;
}
```

### Les attributs

```html
<!-- les attributs globaux -->
<span
  id="pink-floyd"
  class="pink-floyd star music"
  title="Info bulle"
  style="text-decoration: underline; font-wight: bold;"
  onclick="alert('Hello World!'); return false;"
  >Pink Floyd</span
>
```

<span id="pink-floyd" class="pink-floyd star music" title="Info bulle" style="text-decoration: underline; font-wight: bold;" onclick="alert('Hello World!'); return false;">Pink Floyd</span>

Lire + https://developer.mozilla.org/fr/docs/Web/HTML/Global_attributes

### Caractères spéciaux à encoder

En php il existe la fonction `htmlspecialchars()` qui encodera les caractères spéciaux au html

```html
<!-- les caractères à encoder obligatoirement -->
< &lt; > &gt; & &amp;

<!-- Dans certains cas il faudra encoder le guillemet double -->
" &quot;
```

Il existe également la fonction `htmlentities()` qui encode les caractères non ASCI

```html
à &agrave; â &acirc; ç &ccedil; è &egrave; é &eacute; ê &ecirc; ë &euml; ï
&iuml; ô &ocirc; ù &ugrave; &nbsp; Espace insécable &thinsp; Espace fin
<!-- Exemple&thinsp;: -->
```

---

## CSS

### Eléments type block

```html
<!-- les espaces avant/après (leading/trailing) sont ignorés -->
<div> <h1> <section> <article> <nav> <aside> <pre> <hr />
```

### Eléments type inline

```html
<!-- les espaces avant/après (leading/trailing) sont respectés -->
<span>
  <a>
    <i>
      <strong>
        <img />

        <a href="#"> ceci est un lien </a>
        <!-- cela joue surtout un rôle pour le (dé)calage des images -->
        <a href="#">ceci est un lien</a>
        <a href="#">Voici l'astuce</a></strong
      ></i
    ></a
  ></span
>
```

### Sélecteurs

```css
*               /* all elements */
div             /* all div tags */
div,p           /* all divs and paragraphs */
div p           /* paragraphs inside divs */
div > p         /* all p tags, one level deep in div */
div + p         /* p tags immediately after div */
div ~ p         /* p tags preceded by div */
.classname      /* all elements with class */
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

### Formats des couleurs

```css
body {
  background-color: white; /* pratique mais non recommandé */
  background-color: #fff; /* abbréviation de #ffffff */
  background-color: rgb(255, 255, 255); /* 256 niveaux vont de 0 à 255 */
  background-color: rgba(255, 255, 255, 1); /* alpha 1 = 100% */
}
```

### Format des marges (idem pour bordures et hombres)

```css
.marge-1 {
  margin: 1em;
}

.marge-1-2 {
  /* marge haut/bas de 1em + gauche/droite de 2em */
  margin: 1em 2em;
  /* équivalent de */
  margin: 1em 2em 1em 2em;
  /* haut droite bas gauche (sens des aiguilles d'une montre) */
}

.marge-bas-4 {
  /* il est recommandé d'utiliser le propriétés ciblées */
  margin-bottom: 4em;
}
```

---

## DOM

<cite>
Le Document Object Model (DOM) est une interface de programmation normalisée par le W3C, qui permet à des scripts d'examiner et de modifier le contenu du navigateur web1. Par le DOM, la composition d'un document HTML ou XML est représentée sous forme d'un jeu d'objets – lesquels peuvent représenter une fenêtre, une phrase ou un style, par exemple – reliés selon une structure en arbre1. À l'aide du DOM, un script peut modifier le document présent dans le navigateur en ajoutant ou en supprimant des nœuds de l'arbre1.
<cite>

https://fr.wikipedia.org/wiki/Document_Object_Model

<br>

<p>
<img src="assets/img/DOM-model.svg" style="background-color: white; padding: 1em;" />
</p>

---

## JavaScript

### Vanilla

```js
document.addEventListener("DOMContentLoaded", function (event) {
  // Your code to run since DOM is loaded and ready
});

var msg = "OK!";
// /*
msg = "Astuce pour (dé)commenter une section";
// */

console.log(msg);
// Astuce pour (dé)commenter une section
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
"use strict";

$(document).ready(function () {});

/*********************************
 * Mode compatibility (Wordpress)
 * jQuery() est l'équivalent de $()
 *********************************/

(function ($) {
  // here you can call jQuery via $
  // and your variables are isolated
  $(function () {
    // this is a shortcut to $(document).ready()
    // and will be executed when DOM is ready
  });
})(jQuery);
```

### Expression régulières (RegExp)

**Le super "Rechercher/Remplacer" hérité du langage PERL**

N'aura rien de régulier à votre sens, mais un incontournable !

## Format des images

- Portrait : vertical
- Paysage : horizontal

Par convention les images destinées à l'affichage sur écran sont déclarées à 72dpi (Digit Per Inch = PPP - Points Par Pouce).<br>
C'est juste une convention sans trop d'importance, nottez que si on mesure la taille d'une image en pixels (px) le PPP n'a aucune incidence sur la poids de l'image. (Cela peu uniquement influencer la taille de limage imprimée, pour l'affichage à l'écran ce paramètre est généralement ignoré.)

### Tailles courantes

- 640 x 480
- 720 x 480
- 800 x 600
- XGA : 1024 x 768
- HD 720p (0.9K px): 1 280 × 720
- **Full HD FHD (2K) 1080i : 1 920 × 1 080**
- UHD (4K) 2160p : 4 096 × 2 160

#### JPG (lossy)

Le format le plus commun, idéal pour les photos et les visuels très riches en couleurs.

La compression excessive entraîne des effets de moirage.

#### PNG-8 (lossless)

Le format recommandé pour les graphiques simples, les icônes et les logos.

Attention, la transparence sera crénelé tout comme avec le format GIF. (càd que la transparence sera en "tout ou rien" telle coupé au ciseaux)

#### GIF (lossless)

Pour toutes les images animées. (Format non libre de droits)

#### PNG-24 (lossless)

Idéal si vous cherchez un effet de transparence ou pour les images complexes.

La transparence (aussi dit couche alpha) peut être définie de façon progressive.

#### SVG

Un format vectoriel recommandé pour les images vectorisées, vous pouvez ainsi en changer le format sans perdre en qualité. Format puissant permettant animation et interactivité.

Pour son usage dans wordpress il vous faudra un plugin.
Je vous recommande [SVG Support](https://fr.wordpress.org/plugins/svg-support/)

#### WebP

Bien moins connu, en fait vous profitez de ce format sûrement à votre insu.

Ce format proposé par Google supporte les format _lossless_ et _lossy_ et offre des performances de compression supérieurs de 30 à 50% au JPEG ou PNG.

N'étant pas supporté par tous les navigateurs le format est généralement implanté à la volée, càd que les images sur le site dont vous voyez le nom se terminer par un .jpg peuvent avoir été transmis à votre navigateur au format WebP.

Pour vos sites wordpress, je vous recommande le plugin [WebP Express](https://wordpress.org/plugins/webp-express/)

Aujourd'hui (2021) on estime que 80+% des visiteurs utilisent un navigateur qui supporte ce format.<br>
Les versions actuelles de Chrome, Firefox, Safari, Opéra et Edge supportent ce format.

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


# Active l'auto index
Options +Indexes

# pour le désactiver et éviter qu'on puisse parcourir le contenu des répertoires
# Options -Indexes

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
