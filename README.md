

# cms-survey

il y en a un à part qui peut aussi jouer le rôle de grepasjs, et il a un composant HEADLESS CMS, mais c'est clairr vu mes premières utilisations, que c'est du API-based CMS (et non du git based ) : 

* apostrophe CMS
* une recette pour installer apostrophe :  https://github.com/apostrophecms/apostrophe-sandbox


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


