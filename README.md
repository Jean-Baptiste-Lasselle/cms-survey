

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


