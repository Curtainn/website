---
date: 2024-12-17T05:59:11-05:00
draft: false
title: "Réponse à incident multi-acteur"
cover:
    image: img/top-section-bg.jpeg
    alt: 'image'
    caption: 'first image'
tags: ["Technical concepts", "Incident Response", "Multi-Treat"]
categories: ["CTI"]
---

# Préface
L'article qui va suivre vise à détailler comment réaliser une réponse à incident capable de distinguer les traces et chemins de compromission de multiples attaquants se chevauchant dans le temps et l'espace.

# Analyse conceptuelle
## Comportement-based
Les réponses à incident traditionnelles se reposent dans la quasi totalité sur des artefacts bruts collectés lors de l'investigation numérique. Néanmoins, nous pensons qu'il est plus pertienet d'étudier les comportements des individus. Pourquoi ?

Les artefacts, outils, matériels... peuvent varier dans le temps, de part l'évolution des technologies, des stratégies d'attaques ou part le partage de ressource. De ce fait, ces artéfacts gardent-ils toujours une valeur aussi significative ? Pas vraiment.
A l'inverse, le comportement reste inhérent à une personne (physique ou morale). Les procédures, mode opératoires, éléments d'adaptation, tout ces points représentent des schémas de pensée propres et immuable à un entité. De plus, sur une vision court termiste, ces éléments sont très difficiles à changer et même occulter de par leur inhérence. Nous pourrions donc imaginer que le comportement soit une empreinte plus pertinente pour comprendre et caractériser un acteur.

C'est avec cette idée que la suite de l'analyse va tenter de proposer comment traduire les comportements obesrvés à partir des artéfacts collectés lors des investigations. En réalisant cette traduction, nous espérons bien élargir la simple donnée brute, propre à la réalité de la cyber-attaque, par une dimension plus qualitative de l’analyse en intégrant une contingente.

## Attribution des activités
L’un des critères de conception de la solution d'attribution est l'automatisation de l'attribution des activités aux différents acteurs. Pour atteindre cet objectif, nous avons choisi d'utiliser l'intelligence artificielle, en particulier le Deep Learning.

Le Deep Learning permet d'apprendre à partir de données complexes, ce qui constitue une alternative aux choix manuels effectués par des analystes experts dans des tâches de classification. Grâce au Deep Learning, il est possible de maintenir un niveau de précision acceptable tout en réduisant la lourdeur d'une exécution manuelle.

Cependant, un inconvénient majeur du Deep Learning réside dans le volume important de données qu'il est nécessaire de traiter pour classer correctement les activités malveillantes. La qualité des données d'apprentissage est cruciale pour obtenir des prédictions fiables. L'efficacité de l'apprentissage dépend de la diversité des données. En cas d'activités liées à des menaces persistantes avancées (APT) non détectées ou lorsque le modèle ne maîtrise pas suffisamment ces activités, nous regrouperons ces APT non identifiées dans une catégorie spécifique intitulée « APT inconnue ». Cela permet de limiter le risque d'une réponse incorrecte face à des incertitudes (données non représentatives, absence de données spécifiques, etc.).

## Variables comportementales des artéfacts
Quelles données pourraient nous informer sur les biais comportementaux des attaquants ?
- Time to encrypt : le temps attendu entre la compromission du SI et le passage au chiffrement des données 
- Time to expand : y'a-t-il eu une attente avant un potentielle latéralisation ?
- Time to persist : à quel moment de la compromission y'a-t-il eu installation de la persistance ?
- Type de persistance
- Durée de la session
- Nombre d'IPs utilisées
- Fuseau horaore d'activité
- Ressources visées
- ...

Cette liste non exhaustive peut nous permettre de construire un jeu de donné de base. Les données pourraient ainsi se baser sur des compromissions passées.

## Solution conceptuelle
Ainsi, nous aurions une solutions qui :
1- Récolte les artéfacts initiaux (@IP, empreintes SSH, hashs de fichiers, timestamp, outils, etc...)
2- Calcule les variables comportementales (Time to encrypt, Time to expand, Time to persist, etc...)
3- Communique avec un modèle d'IA qui gèrerait l'attributions des schémas comportementaux à une APT

# Modélisation des processus adverses
Nous allons ici prendre exemple sur APT28 et APT29.

Afin de mieux comprendre les différences entre les réactions de Fancy Bear (APT28) et Cozy Bear (APT29) lors d'une attaque, il est important de connaître la réputation de chacune de ces APT.

APT28 (Fancy Bear) : Associé à l'armée russe (GRU), ses techniques d'attaque sont plutôt bruyantes et incluent des méthodes telles que le spear-phishing, l'exploitation de failles récentes et les campagnes de désinformation.

APT29 (Cozy Bear) : Associé aux services de renseignement extérieur russes (SVR), ce groupe privilégie des méthodes plus discrètes et de long terme, telles que le maintien d'un accès discret au système et l'exfiltration de données sensibles.

Un exemple marquant des cyberattaques est celui qui a visé le Comité National Démocratique (DNC). Les attaques qui ont pénétré le système informatique du DNC ont commencé en 2015. L'attaque de Cozy Bear a débuté à l'été 2015, tandis que celle de Fancy Bear n'a commencé qu'en avril 2016. Ce n'est qu'après l'attaque de Fancy Bear que la compromission du système est devenue évidente.

**Pour plus d'informations voir** [ici](/ingerence_russe_fr.md) 

Pour distinguer les réponses d'APT28 et d'APT29 face à des mesures de défense, il est raisonnable de se baser sur leurs différences fondamentales en termes de tactiques, techniques et procédures (TTPs).

Par exemple, lorsque leurs infrastructures de command and control (C2) sont bloquées, leurs réactions divergent :
- APT28 réagit de manière rapide et visible, en diversifiant souvent ses outils et en configurant à la hâte des infrastructures de secours.
- APT29, au contraire, adopte une posture plus discrète, reposant sur des infrastructures redondantes. Dans certains cas, ce groupe prend aussi des périodes de latence pour évaluer les impacts avant de réagir.

Dans la même logique, l'implémentation rapide de correctifs de sécurité pousse APT28 à intensifier ses efforts d'exploitation avant que les défenses ne prennent effet. En revanche, APT29 se tourne vers des tactiques alternatives, comme l'exploitation de vulnérabilités peu documentées ou présentes dans ses propres bases.

L'utilisation de leurres, comme des faux documents sensibles contenant des balises traçables ou des vulnérabilités simulées, entraîne également des réponses différentes :
- APT28 extrait une quantité massive de données, dont certaines, en réalité, sont inutilisables.
- APT29, de son côté, procède à une analyse minutieuse pour exfiltrer uniquement les informations jugées stratégiques et pertinentes.

La publication d'indicateurs de compromission (IOCs) met en lumière leur capacité d'adaptation :
- APT28 recadre facilement ses outils pour contourner les artefacts de défense.
- APT29, quant à lui, déploie davantage d'astuces pour camoufler et chiffrer ses communications afin de rester hors de vue.

Enfin, une analyse temporelle et géographique de leurs opérations révèle d'autres différences :
- APT28 semble opérer de manière plus visible, souvent en phase avec les horaires de bureau russes.
- APT29, par contre, se cache derrière des relais géographiques et agit de manière plus méthodique.

## IOM axée sur le comportement
L'analyse comportementale vise à exploiter les comportements, motivations ou faiblesses perçues des adversaires. Elle consiste à analyser les schémas d'action prévisibles, les cycles d'opérations ou les comportements en réponse à des événements défensifs afin de les influencer ou de les amener à tomber dans un piège.

Dans le cadre de l'attaque contre le DNC, l'analyse des comportements de APT28 et APT29 permet de cibler à la fois l'action choisie et ses effets. Face aux réponses rapides et bruyantes d'APT28, une action efficace consisterait à installer des honeyfiles sur le réseau, remplis de données fictives, telles que des projets politiques ou des fuites d'informations stratégiques inventées. Ces données sont faciles à détecter par les outils d'exfiltration habituels du groupe, ce qui permet de les utiliser comme appâts. En intégrant des balises traçables dans ces documents, il devient possible de suivre en temps réel l'exfiltration et l'exploitation de ces informations, détournant ainsi l'attention d'APT28 des données sensibles réelles, tout en révélant ses infrastructures d'exfiltration et ses capacités réactionnelles.

Dans le cas d'APT29, son comportement discret et méthodique peut être exploité de manière manipulatrice. Par exemple, en insérant dans les systèmes internes des comptes de messagerie fictifs simulant des échanges stratégiques critiques, il est possible de capter son attention et de l'inciter à investir des ressources pour les analyser. Le temps consacré à cette tâche sera minutieusement surveillé pour obtenir des renseignements précieux sur ses méthodes d'accès, d'extraction et de déchiffrement, tout en le maintenant éloigné des cibles réelles. Ce scénario permet de détecter ses mouvements et de mieux anticiper ses actions. Ces deux stratégies exploitent de manière optimale les différences comportementales entre les groupes dans un but défensif.

L'IOM comportementale peut donc être très bénéfique si les acteurs sont identifiés à l'avance. Cependant, dans le cadre d'une intrusion multi-acteurs, il est crucial d'isoler l'influence exercée sur chaque groupe. Par exemple, rendre les honeyfiles visibles uniquement aux sessions attribuées à APT28 évite de déclencher les soupçons d'APT29.

## IOM axée sur les motivations
Cette approche se concentre sur les motivations de l'adversaire, telles que le renseignement stratégique, la déstabilisation politique ou la monétisation des attaques. En jouant sur leurs motivations, nous pouvons détourner leur attention vers de fausses cibles ou les amener à gaspiller du temps et des ressources dans des efforts inutiles.

APT28 est principalement motivé par le désir de perturber les processus politiques ou de produire un effet immédiat sur l'agenda public. Dans cette perspective, une stratégie efficace d'influence consisterait à fournir aux organisations ciblées des données faussement compromettantes, fabriquées de toutes pièces, sur des personnalités ou des institutions politiques. En chargeant les systèmes vulnérables de faux documents révélant des faits inventés ou des scandales, il devient facile de les pousser à une diffusion précipitée. Cependant, cela comporte des risques : une campagne trop visible pourrait être rapidement démasquée, ce qui nuirait à l'efficacité de l'opération. Si l'interlocuteur diffuse l'information fausse avant qu'elle ne soit reconnue comme telle, la manipulation perd son impact, car elle repose sur la rapidité et la justesse des cibles publiques.

## Conclusion
L'analyse conceptuelle et la modélisation des processus adverses présentées dans les sections précédentes ont permis d'établir les bases théoriques nécessaires à une attribution précise et à une gestion efficace des réponses aux menaces. En examinant les différences comportementales entre APT28 et APT29, nous avons mis en lumière les éléments clés qui permettent de concevoir des stratégies d'influence adaptées à leurs profils respectifs.
