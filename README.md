

# cms-survey

il y en a un à part qui peut aussi jouer le rôle de grepasjs, et il a un composant HEADLESS CMS, mais c'est clairr vu mes premières utilisations, que c'est du API-based CMS (et non du git based ) : 

* Apostrophe CMS https://github.com/apostrophecms/apostrophe  
* La partie CMS Headless aposrophe : https://github.com/apostrophecms/apostrophe-headless
* Une recette pour installer apostrophe :  https://github.com/apostrophecms/apostrophe-sandbox  
* Un article pour essayer de faire lien avec GraphQL // https://medium.com/@apostrophecms/apostrophecms-3-0-the-work-begins-5cd7c95024b7
* une bonne vidéo sur apostrophe https://www.youtube.com/watch?v=A8R2szAFul8
* il y a une opportunité là : 
  * dans la doc officielle , il y a une partie qui parle du déploiement de l'infra cibel déploiement https://apostrophecms.org/docs/tutorials/intermediate/deployment.html
  * cette partie technique : montre qu'il n'y a pas de provision prête pour docker, je peux laider là dessus
  * il recomande d'utiliser NGINX et [mechanic](https://www.npmjs.com/package/mechanic), mechanic lui servant à mettre à jour la configration de NGINX, à chaque nouveau dépoiement de service (apoarrement fait par apostrophe lui-même) : et pourquoi pas traefik, parceque l'on voit que `mechanic` permet de faire des conf load balancer avec NGINX (et le cas est intéressant : modifier la conf NGINX depuis l'application elle-même...)
  * autre chose, dans la même page de dock, checher `Minifying assets` : à cet endroit, il se trompe complètement, il dfait comme si l'environnement de déploieemnt du site web géénré avec Apostrophe, devait être hébergé sur ce même serveur... Ou alors il s'agit d'une sorte d'envrionnment de preprod... Sûr qu'il y a un truc à ajuster avec les pipelines là
  * soit dit en passant, il n'a rien concernant ansible nonplus, iun vrai coup de main à donner.
  
  


# Headless

Headless CMS case study comparing and uses cases of products in that galaxy

## Team

* netlify (trè sbonne intégration avec  `Gitbook` / avec Jekyll)  (celui-là je vais l'utiliser pur les workflow GIT, je pense pour les pieplines, il est très orienté git workflow)
* gatsby (see. https://github.com/Jean-Baptiste-Lasselle/gatsby-contentful-starter )
* https://github.com/directus/directus (celuilà j'ai beaucoup aimé la clareté de la doc, et il y a la quesytion de la délégation des permissions, à l'API gateway Gravitee.io
* https://github.com/agentejo/cockpit
* https://github.com/dadi/api


## Familles

Il existe aujourd'hui 2 grands types de CMS : 
* les _`Git based CMS`_ :  Netlify en fait partie
* les _`API-driven CMS`_ : 
  * Strapi en fait partie , 
  * ouh celui là a l'air très très bon : https://github.com/ponzu-cms/ponzu 
  * mais il y a aussi https://github.com/agentejo/cockpit  
  * https://github.com/directus/directus
  * et celui-là je l'ai bien aimé dès le départ : https://github.com/daptin/daptin   la doc est bien orientée API, et immédiate citation de `GraphQL`
  

### Netlify

Excellent ! Le framework va chercher le contenu sur GIT !!! selon une source, il apparaîtrait que Netlify ne s'intègre que sur GITHUB, et pas encore GITLAB etc... pour l'authentification (ils parlent de GIT-GATEWAY), parce qu'il s'agit de la gateway de l'API gtihub

### Dato CMS et Vue.js (nuxt.js)

* https://www.youtube.com/watch?v=KdOQhTLHT0U
* [tutoriel github / test data CMS with VueJS](https://github.com/mcpll/dato)
* https://github.com/biilmann/dato-cms-deploy-demo
* https://github.com/javierarques/react-datocms   Example React app fetching dato from datocms
* stop : dato n'est pas open source
* dato est payant


# Okay 1ere reflexion

il y a 2 choix : 
* soit on fait une vraie SPA type angular meteor, et alors le HTML et le CSS sont générés pendant le Run, par la SPA, et alors le workflow repose sur el fait de pouvoir générer une SPA  à partir d'un template en pur HTML, et l'opération inverse (aspirer le client web, comme on aspire un site web)
* soit on fait un worflow : templating statique grapesjs => génération d'un template valide pour gatsby, à partir du template HTML5  => traitement gatsby / netlify pour générer un site statique à partir du contenu stocké dans une API => aspiration du html css pour les [pages de référence du template HTML5](#notion-de-page-de-reference) => templating HTML5  statique grapesjs 

À propos des SPA , et de Gatsby (à étendre à tous ces CMS Headless, qui génère des sites statiques surla base d'un contenu envoyé par une API, par exemple unsite régénéré toutes les nuits), un avis d'un des membres de l'équiep Gatsby qui confirme mon analyse : 

[![équipe gatsby confirme mon analyse](https://github.com/Jean-Baptiste-Lasselle/cms-survey/raw/master/documentations/images/CMS_GATSBY_AND_SPA_2019-03-25%2001-32-03.png)](https://github.com/gatsbyjs/gatsby/issues/3539#issuecomment-357793051)

### Notion de page de référence
 
Notion de page de référence : 

* reliée à une requête HTTP précise à envoyer, et le HTML est aspiré comme ça, même s'il y a une pagination et des "résultats suivants" à visulaiser
* mais il reste la question de savoir quel est l'unité réptable de référence, pour cela grapesjs permetrait d'utiliser les classes CSS 
* donc l'idée est qu'il faudrait ajouter une classe CSS qui indique lapartie répétable sur chaque éléent répété.
* en fait il faudrait des classes CSS qui indiquent à l'utilisateur grapesjs, quel sont les éléments de pages qui seront nourris par l'API netlify derrière.
* ça vaudrati le coup de faire le tests du même use case avec le duo gatsby / strapi, mais j'aurais le même problème de désignation des contenus répétables.
* pour moi , c'est l'utilisateur grapesjs, qui doit indiquer qu'un conteneur doit être nourris par une API, et les classes CSS qu'il applqiue, me permettent de repérer les partiesà générer avec gatsby / netlify
* Quelle est la forme des GAtsby templates ? Comnt créer un `Gatsby Starter` :
  * https://medium.com/@emasuriano/how-to-create-a-gatsby-starter-e7d53083a880
  * 

Le cycle devient : 

* tédition HTML5/css grapesjs : la personne doit être formée à marquer les éléments nourris par l'API, à l'aide d'une classe css, que l'appellerai `.garnison`. Le template HTML attapé par le designer, qu'il a mis dans un repo git, est alors automatiquement scanné, pour voir s'il contient une classe CSS déclarée avc le nom `garnison` : 
  * s'il en contient uen, le designer est alerté, et il lui et demandé d'utiliser non pas le nom de classe `.garnison`, mais le nom de classe `.garnison-$GARNISON_ID`, où `GARNISON_ID` est une valeur aléatoire générée, pas trop compliquée (4 chiffres devraient suffire, sinon le designer contacte l'équipe dev pour modifier le tempalte HTML5 avant de re partir dans el workflow), et qui est générée autant de fois que nécessaire, pour qu'il n'ya ait aucune redondnance avec les identitifaints utilisés dans le 
  * bon, il faudra gérer la non collision des noms, en la repérant, et en proposant un `GARNISON_ID` généré, ou en propsant à l'utlisateur de saisir une valeur lui même pour `GARNISON_ID`, la saisie d'clenche le scna pour confirmer à l'utilisateur qu'il a bien choisis un identifiant de classe css sans collision ave le template.
  * Ok, maintenant que cet identifiant propre à la chaine de montage (pipeline), est apposé par le designer pour indiquer les parties CSS qu'il voit nourries par une API de content management  (Content delivery API...?), il peut utilsier d'autres noms de classes pour stipuler exactement, pour chaque API REST, dans quel bloc va quel champs;
  * ok, donc on aurait des classes CSS nommeés du genre `.garnison-$GARNISON_ID .api-id-$NETLIFY_API_ID .api-field-$API_FIELD_ID` : 
  
  ```html
<article class="forecast" >
    <h1>Weather forecast for Seattle</h1>
    <!-- I'd say export NETLIFY_API_ID=bulletin.forecast-api.io , you ...? -->
    <article class="day-forecast garnison-$GARNISON_ID api-id-$NETLIFY_API_ID">
        <!-- I'd say export API_FIELD_ID=forecast_datetime, name of the field created with Netlify, you ...? -->
        <h2 class="api-field-$API_FIELD_ID">03 March 2018</h2>
        <!-- I'd say export API_FIELD_ID=forecast_bulletin, name of the field created with Netlify, you ...? -->
        <p class="api-field-$API_FIELD_ID">Rain.</p>
    </article>
</article>
  ```
  
  pourrait générer : 
  
  ```html
<article class="forecast">
    <h1>Weather forecast for Seattle</h1>
    <article class="day-forecast">
        <h2>03 March 2018</h2>
        <p>Rain.</p>
    </article>
    <article class="day-forecast">
        <h2>04 March 2018</h2>
        <p>Periods of rain.</p>
    </article>
    <article class="day-forecast">
        <h2>05 March 2018</h2>
        <p>Heavy rain.</p>
    </article>
</article>
  ```
  
* l'équipe de dev, sa
*   => traitement gatsby / netlify pour générer un site statique à partir du contenu stocké dans une API => aspiration du html css pour les [pages de référence du template HTML5](#notion-de-page-de-reference) => templating HTML5  statique grapesjs 
