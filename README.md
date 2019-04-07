# TODO du mataîng

* pipeline nodejs
* pipeline meteor / enchaîné avec / yes oui can
* pipeline robots de fusées
* grapesjs storage manager
* battle test nico's code
This is a footnote.

# Mesh API Driven?

https://getmesh.io/docs/getting-started/


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
  
  
 Pour régler la question strapi, je vis le balancer dans un réseau complètement fermé, et analyser si ej peux reconstruire un code source à partir duquel faire le build , et obtenir le poulet que j'ai fait fonctionner dans un résau fermé Ensuite, je vais comparer le code source que j'ai reconstitué, (ou exposer les obestructions à retrouver le code source), à la version exposée https://github.com/strapi/strapi, qui d'apreès son `README.md` permet de reconstruire l'artefact distribué par `npm install -g strapi@latest`
  


# Headless

Headless CMS case study comparing and uses cases of products in that galaxy

## Team

* netlify (trè sbonne intégration avec  `Gitbook` / avec Jekyll)  (celui-là je vais l'utiliser pur les workflow GIT, je pense pour les pieplines, il est très orienté git workflow)
* gatsby (see. https://github.com/Jean-Baptiste-Lasselle/gatsby-contentful-starter )
* https://github.com/directus/directus (celuilà j'ai beaucoup aimé la clareté de la doc, et il y a la quesytion de la délégation des permissions, à l'API gateway Gravitee.io
* https://github.com/agentejo/cockpit : exclut, je ne veux pas voir de PHP.
* https://github.com/dadi/api : C'est bien un CMS pur API driven : 
> COPE stands for Create Once, Publish Everywhere  (cf. https://dadi.cloud/en/knowledge/web-services/api-first-and-cope/ )

* getcockpit : an API driven CMS
* forestry : a CMS.... of what kind?

# Mes préférés : dadi et daptin

## Dadi 

J'aime : 

* Le fait qu'il font une vraie solution pure API-first
* Il est développé, et tous ses composants, en `NodeJS`
* qui est clairement dans l'apporche que je veux mettre en oeuvre (COPE)
* Et dis-donc, ils fournissent aussi plusieurs choses, sur github : 
  * Un CDN que je peux utiliser dans mes pipelines de chevaux ! https://github.com/dadi/cdn (j'ai aussi https://github.com/Jean-Baptiste-Lasselle/fruity-unpkg.com pour cdn des pipelines)
  * https://github.com/dadi/
  * Documentation automatique des APIs générées avec dadi : https://github.com/dadi/apidoc  (à modifier pour faire une génération de documentation de type swagger Open API (et bingo, je ne suis pas le seulà le penser : https://github.com/dadi/apidoc/issues/11 )

La solution me paraît bien plus simple que certaines autres dantesques (pour quelque chose d'aussi spécialisé et clair, fonctionnellement, on veut pouvoir créer des APIs, en veux-tu en voilà)

L'issue https://github.com/dadi/apidoc/issues/11 laisse à penser que DADI est OpenAPI compliant, with guarantee


Par contre l'essai avec DADI API est fort encourageant : https://github.com/Jean-Baptiste-Lasselle/dadi-cms/



## Daptin


Il semblent avoir les mêmes caractérisques que DAID, masi la différence, c'est que j'ai immédiatement trouvé : 
* un déploiemnt docker
* un déploiement docker-compose
* un déploiement kubernetes
* cf https://daptin.github.io/docs/setting-up/installation/  (ils ont uune super doc)

et ils sont sacrément bien classés dans le classemnt effetué par les métriques social networking de github

Update !! : cf [`./experiments/daptin/1`](./experiments/daptin/1) J'ai testé le docker-compose, ait réussit à lancer l'application, j'ai pu créer une API, mais lorsque j'ai voulu ajouter des items dans l'API (le modèle était créé), je suis tombé sur un tas de trucs bizarres dans la UI, des éléments de fonctionnements vriaemnt pas logiques, et au final, impossible de créer le moindre item de contenu...



## Familles

Il existe aujourd'hui 2 grands types de CMS : 
* les _`Git based CMS`_ :  Netlify en fait partie
* les _`API-driven CMS`_ : 
  * Strapi en fait partie , 
  * ouh celui là a l'air très très bon : https://github.com/ponzu-cms/ponzu 
  * mais il y a aussi https://github.com/agentejo/cockpit  (exclut, a comme pre-requisistes PHP)
  * https://github.com/directus/directus  (je n'aime pas leurs docs et leurs vidéos trop orientées monde PHP, encore à cause de wordpress)
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
  * ok, donc on aurait des classes CSS nommeés du genre `.garnison-$GARNISON_ID .api-id-$NETLIFY_API_ID .api-field-$API_FIELD_ID`  : 
  
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
  
* l'équipe de dev, avec le template HTML annoté de classes css, reçoit le template et la confguration des classes utilisées pour annoter, et marquer les parties nourries par API. 
* L'équipe de  dev doit mainenant créer une nouvelle version du Gatsby-starter, pour générer le site internet exactement sous la forme statique spécifiéé par le templateHTML. Il manque une chose au template manipulé par l'utilisateur GrapesJS, il doit pouvoir faire un sitemap pour spécifier la nivagation entre les pages; Il spécifie dans GapesJS ce sitemap avec un composant graphique GRapesJS, et derrière ça mets à jour les liens `href` du menu de navigation.
* dans grapesjs, le menu de navigation, s'il y en a un (il y en a toujours un, c'est donc un critère imposé), est lié à une sitemap
* il peut même n'y avoir aucun menu de navigation de prévut dans le design : l'arbre des fichiers `/omega`, je sélectionne une feuille de l'arbre, et je relie la feuille de cet arcbre (le fichier HTML), à un point de navigation d'ans l'arbre `sitemap`
* Donc dans grapesjs, deux arbres présentés, l'arbre stiemap, et l'arbre des fichiers dans `/omega`, on doit lier chaque fichier HTML (pas les css ou images ou fontes ou autre fichiers), à un point de l'rarbre sitemap. Il y a alors toujours l'OPTION, mais cela reste une option, de générer le navbar menu à partir de ces entrées, et cela doit donner lieu à un nouveau composant drag n drop pour `grapesjs`
* mais avec toutes ces infos, plus le marquage CSS, l'équipe de dev a tou ce qu'il faut pour :
  * soit passer à générer une nouvelle version de SPA, avec cette base, et alors il ssavent quelles API utiliser, et les classes CSS leur indiquent le mapping de données avec l'API (_donc les  annotations de classes CSS doivent indiquer la version d'API, idéaleemnt, pour que l'on sache à quelle version d'API est reliée une version `git` d'un template HTML5 envoyé par les business ananlyst, annoté de classes CSS_)
  * soit passer à générer une nouvelle version du projet gatsby, peut-être même de site web, car c'est e gatsby starter qui commence à déterminer quel va être le HTLM5 généré , et alors l'équipe utilise les mêmes annontations pour changer le code source du projet gatsby, afin qu'il génère un contenu différent. Oui non, à chaque fois que l'on modifie le template, il faut faire une nouvelle version de gatsby starter, c'est à dire avoir un template partageable à tous, pour chaque version du site déployé.
 * Je pense que le workflow est de générer le gatsby starter kit au départ, seulement à partir de la toute première version, le template HTML5 chosis au départ; le gatsby starter il y en a plein ici : https://www.gatsbyjs.org/starters?v=2  et en voilà un typique sur github : https://github.com/netlify-templates/gatsby-starter-netlify-cms  
 * donc après avoir fait un starter kit pour ce template HTML5 annoté, je créée un projet `gatsby` avec le starter kit, et j'ai une nouvelle version de ce projet `gatsby`, à coder, pour chaque nouvelle version de template HTML5 annoté de CSS, envoyé par les business analyst avec leur `grapesjs`
 * ensuite on déploie, et les business analyst s'amusent , mais à version d'API fixe, liée à la version de temlate HTML5 q'ils ont fait. Ils changent le contenu de l'API, en fasant du CRUD sur les entrées, sans changer le schema, et relancent la génération `gatsby` avec un bouton refresh site, et le site est régénéré sous leurs yeux ébahis. doncà version d'API fixe, es-ce que je peux leur automatiser le fait que le projet gatsby puisse être automatiqueemnt modifié,si 'on ne modifie aucune annotation "de nourriture par l'API"? c'et ce point qui serait leplus intéressant.
 * enfin, pour ce cycle, j'ai tout de même le cycle comlet, et derrière jepeux faire une app mobile pour envoyer un nouveau post, ...
 * question : comment je fais pour que les Content Delivery API comme cela, soient en mode push, vers le canaux? Pour les sites web,ce doit etre une iterragotation récccurrente, typquement toutes les nuits, pour avoir un contneu frais toutes les nuits, mais cela peut facilement descendre à toutes les heures, à mon avis, en mode continuous delivery. Pour ce qui est des réseaux sociaux, là pour moi, c'est une autre at... Non, il faut une platefore centrale qui orchestre les opérations, les rends transactionnelles, et qui définit des fréquences de mises à jour par canaux,avec un monitoring global sur chaque canal soicial, avec une adaptateur sur chaque canal social 
 
 avec la version de l'API qui correspond à la version du template 

* Les parties nourries par API, ne sont pas forcméent toujpurs des listes, ce peut être un contenu, que l'on veut changer via l'API, pour envoyer les changements en mode multi-canal, via plusieurs sites internet, tous gégéas ave ce modèle gatsby netlify augmenté de grapsjs
*   => traitement gatsby / netlify pour générer un site statique à partir du contenu stocké dans une API => aspiration du html css pour les [pages de référence du template HTML5](#notion-de-page-de-reference) => templating HTML5  statique grapesjs 
* et il faut une orchestration du backup restore principalement des version infra as code gatsby, et des bdd des Content Delivery REST API, quipermetteent de rétablir une version d'API dans un état donné, donc histrique des contenus délivrés.
analytics et SEO à gérer comme d'hab pour spa , et pour les sites statiques, faire appel aux spécialistes, dans le pipe, aucune adhérence ac le travail des designer, et le pipeline de colllaboration avec le dev frontend
* ds tous les cas l'équipe utilisera graphql, pour faire un backend for front end BFFF and Gatsby , au niveau du projet gatsby


# Next Step 

Pour aller plus loin, éclaicir la question `Comment fais-t-on pour modifier le design de la barre de navigation?`, avec Gatsby : 

* https://www.gatsbyjs.org/docs/centralizing-your-sites-navigation/#using-the-header-component-to-display-the-navigation  React et Gatsby....? si je peux coller ça enmeteor, mon problème de référencement est réglé, et si je pex statiquement générer un site SPA, je veux voir le use case...

https://www.gatsbyjs.org/docs/sourcing-from-netlify-cms/  = recette gatsby /netlify

versionnig des models api créées dans netlify : 

* je ne sais pas encore comment versionner les models (les modèles de données de chaque endpoint de l'API, le swagger...)
* je sais ceci quenetlify cms est spécifiquement prévu pour les générateurs de sites statiques comme gatsby, je cite : https://github.com/netlify/netlify-cms#netlify-cms : 

> A CMS for static site generators. Give non-technical users a simple way to edit and add content to any site built with a static site generator

* Je cite https://www.netlifycms.org/docs/intro/#netlify-cms-vs-netlify : 
> The folks at Netlify created Netlify CMS to fill a gap in the static site generation pipeline. 
> With this in mind, you can:
> 
> * Use Netlify CMS without Netlify and deploy your site where you always have, hooking up your own CI, site hosting, CDN, etc.
> * Use Netlify without Netlify CMS and edit your static site in your code editor.
> * Or, use them together and have a fully-working CMS-enabled site with one click!
> 

_Leur objecif est donc bien un **pipeline**, qui implique des "**non-technical users**"_


* Pour le workflow j'ai aussi une bonne ressource sur la phase " générer une SPA / applicationangular à partir d'un template pur _{HTML / CSS / images / fonts}_ : 

  * https://blog.angularindepth.com/creating-your-own-application-template-for-angular-cli-95e22319cc24


# Une présentation de référence

La vidéo https://www.youtube.com/watch?v=KX4G49ZrvY0 présente très bien le concept de CMS Headless, le contexte et les raisons de son émergence.

Clairmeent, l'enjeu est au niveau d la collaboration entre Infra et Dev, et la présentation montre comment ces dernières années,  celui qu souffre de la situation est le client.


* Pour les headless CMS, il y a 2 modèles, les Git based, et les API driven
* La vidéo https://www.youtube.com/watch?v=KX4G49ZrvY0 présente 2 worklflow :
  * un workflow qui vaut pour les stacks reposant sur un `Git based  CMS`
  * un workflow qui vaut pour les stacks reposant sur un `API driven CMS`
* Le gars dans https://www.youtube.com/watch?v=KX4G49ZrvY0 montrent en quoi ces 2 approches apportent un gain en sécurité, en "mental load" (c'est à dire à quel pint il est facile de se plonger dans le stack technos) 
* il dit qu'il y a un gain en sécurité, par ceuqe dasn les 2 cas, on a exaxctement 4 points bien précis à sécuriser, et que dans tous les cas, si un point est compromis, la compriissions poeut être compartimentée comme dans les sous marins.
* un autre argument pour la sécurité : le problème avc ces _plugin-based solutions_, (wordpress a un modèle économique basé sur les plugins wordpress) , c'est que le datacenter, s'il fait confiance à wordpress en termes de sécurité, mais les clients voudront, sur une base imprévisible, spécifique à chaque user, et sans dialogue avec le datacenter, déployer des plugins wordpress qui peuvent tous petentiellement amener leurs failles de sécurité. Les 2 approches CMS Headless, permettent de se débarrser de cela, il n'y a plus de familles de plugins qui peuvent être déployés par les clients du datacenter.
* Pour montrer le gain en "mental load",il faudrait fair le comparatif entre les vieux workflows CMS, et ces deux nouveaux types de workflow.

IL FAUT , expérimenter au moins un workflow dans chacune des ces deux approches.

> Security for the CMS becomes a no-brainer

#### Vocabulaire :  The JAM Stack

Typiquement associé au mode du dev front end , pas forcément unqiuement les CMS : 

> [JAMstack](#): noun `\’jam-stak’\`
> Modern web development architecture based on client-side JavaScript, reusable APIs, and prebuilt Markup.

Sur https://jamstack.org , on trouve : 
* un livret de bonne pratiques. https://jamstack.org/best-practices/
* d'excellent  exemples https://jamstack.org/examples/
* de l'organisation évènementielle https://jamstack.org/community/  (u meeetup par grande ville, il y a Londres et Paris.



