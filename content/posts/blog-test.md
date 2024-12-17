---
date: 2024-12-17T05:59:11-05:00
draft: false
title: "Comment l'ingérence russe a soulevé le cas des présences hybrides"
cover:
    image: img/top-section-bg.jpeg
    alt: 'image'
    caption: 'first image'
tags: ["Politic ingerance", "APT28", "APT29"]
categories: ["CTI"]
---

# Étude de cas

## Le cas DNC

### Contexte
Le DNC (Democratic National Committee) est un organisme politique américain voué à la direction du Parti démocrate.

Les agences de renseignement américaines ont attribué l'attaque à deux groupes russes :
1. **APT28 (Fancy Bear)** : apparenté au GRU, le service de renseignement militaire russe.
2. **APT29 (Cozy Bear)** : lié au FSB, le service de sécurité intérieur de la Russie.

L'objectif de ces deux acteurs était de saboter la campagne présidentielle américaine de 2016 afin de favoriser l'élection de Donald Trump en discréditant Hillary Clinton. Ces conclusions sont détaillées dans le rapport du procureur spécial Robert Mueller, publié en avril 2019, qui affirme que « l’État russe s’est immiscé dans l’élection présidentielle de 2016 de façon systématique ».

---

### Analyse APT28 dans le cadre du DNC

APT28, également connu sous le nom de Fancy Bear, est un groupe de cyberespionnage associé au GRU (Direction principale du renseignement militaire russe). Actif depuis le milieu des années 2000, ce groupe est réputé pour ses campagnes d'espionnage contre des cibles gouvernementales, militaires et médiatiques.
APT28 se spécialise dans des attaques ciblées visant à collecter des informations sensibles et à influencer des processus politiques. Ses activités incluent également des campagnes de déstabilisation via des fuites de données.


#### Tactiques et modes opératoires

1.	Reconnaissance avancée :
- Collecte d'informations sur les infrastructures cibles grâce à des bases de données compromises et à l'ingénierie sociale.
- Analyse des systèmes pour identifier des points faibles.

2.	Phishing ciblé (T1566) :
- Campagnes sophistiquées de spear phishing, avec des pièces jointes ou liens malveillants, souvent conçus pour imiter des communications légitimes.
- Exploitation de thèmes spécifiques pour inciter les utilisateurs à ouvrir les messages (par exemple, des courriels liés à des événements politiques ou militaires).

3.	Exploitation des vulnérabilités (T1190) :
- Utilisation de failles connues dans des logiciels comme Microsoft Office ou Adobe Flash pour déployer des charges utiles malveillantes.
- Développement d'exploits sur mesure pour contourner les protections de sécurité.

4.	Logiciels malveillants personnalisés :
- APT28 utilise des outils comme X-Agent, Sofacy, et Zebrocy, conçus pour l'espionnage, la collecte de données, et la persistance.

5.	Fuites de données et déstabilisation :
- Publication des données exfiltrées via des plateformes comme DCLeaks ou WikiLeaks dans le but de perturber les cibles.


#### Points forts d’APT28

1.	Exploitation rapide des vulnérabilités :
- Utilisation de failles connues combinée à une ingénierie sociale efficace.
- Déploiement d'outils de collecte de données très sophistiqués.
2.	Stratégie d'influence politique :
- L'objectif d'APT28 ne se limite pas à l'espionnage. Il s'étend à l'utilisation des données volées pour perturber les processus politiques et manipuler l'opinion publique.
3.	Portée mondiale :
- APT28 cible un large éventail de secteurs, incluant les gouvernements, les organisations militaires, et les médias.
---

### Analyse APT29 dans le cadre du DNC

APT29, également connu sous le nom de Cozy Bear, est un groupe de cyberespionnage étroitement lié au FSB (Service fédéral de sécurité russe). Ce groupe est connu pour ses campagnes sophistiquées ciblant principalement des gouvernements, des organisations de recherche, et des institutions internationales.
APT29 se distingue par son approche discrète et sa capacité à maintenir des accès persistants dans les systèmes compromis. Contrairement à APT28, APT29 privilégie les actions de surveillance sur le long terme pour collecter des informations stratégiques.

#### Tactiques et modes opératoires
1.	Reconnaissance avancée :
- Exploitation des vulnérabilités dans les systèmes exposés.
- Collecte d'informations sur les infrastructures cibles.
2.	Phishing ciblé (T1566) :
- Envoi d'emails de spear phishing contenant des pièces jointes malveillantes ou des liens vers des sites frauduleux.
- Utilisation de thèmes crédibles pour tromper les employés, comme des messages liés à la sécurité ou des communications gouvernementales.
3.	Exploitation des vulnérabilités :
- APT29 utilise des exploits pour tirer parti des failles non corrigées dans les logiciels et les infrastructures. Des campagnes notables ont visé des solutions telles que SolarWinds et Microsoft Exchange.
4.	Outils malveillants sur mesure :
- Déploiement de logiciels malveillants avancés comme Cobalt Strike, WellMess, et WellMail, qui permettent de collecter et d'exfiltrer des données sans éveiller les soupçons.
5.	Techniques d’évasion (T1562) :
- Utilisation de logiciels légitimes détournés pour éviter la détection.
- Suppression des traces d'activité après l'exfiltration des données.

#### Points forts d’APT29
1.	Sofistication technique :
- Exploitation de failles complexes dans les chaînes logicielles (supply chain attack).
- Développement d'outils sur mesure pour des attaques de grande envergure.
2.	Discrétion :
- Techniques avancées d’évasion pour minimiser les risques de détection.
- Suppression des journaux et utilisation de logiciels légitimes pour cacher leurs traces.
3.	Portée globale :
- Impact mondial avec des cibles dans plusieurs secteurs, notamment la défense, la santé, et la recherche

---

### Timeline

- **Juin 2015** : APT28 obtient un accès au réseau du DNC.
- **25 septembre 2015** : Un agent du FBI prend contact avec le responsable de la gestion du réseau du DNC pour signaler des activités suspectes sur leur réseau. Ces actions malveillantes étaient menées sous le pseudonyme "Dukes", couramment utilisé par des acteurs cyber russes.
- **Mars 2016** : Un membre de la campagne de Hillary Clinton est compromis par un email de phishing issu d'une campagne d'APT28.
- **15 juin 2016** : Le GRU revendique sa responsabilité dans l'attaque du DNC et publie des documents internes contenant notamment des rapports de recherche sur les opposants politiques, des informations sur les donateurs de campagne, et des correspondances internes. Cette fuite remet en question l’impartialité du DNC.
- **29 juin 2016** : Le DCCC (Democratic Congressional Campaign Committee) annonce avoir été à son tour victime d'une attaque attribuée à une entité russe.
- **20 septembre 2016** : L’entité russe, identifiée comme le GRU, copie près de 300 Go de données du réseau du DNC en vue de leur exfiltration.
- **7 octobre 2016** : Le DHS et le Bureau du Directeur National du Renseignement (ODNI) publient un communiqué accusant le gouvernement russe d'avoir orchestré ces attaques pour interférer dans l’élection présidentielle américaine de 2016.
- **29 décembre 2016** : Les activités de cyberespionnage s’étendent à 21 infrastructures liées aux élections, selon le Comité de renseignement américain (rapport du 21 juin 2017).

---

## Analyse des données et résultats obtenus

### Tactiques employées par APT28

1. **Reconnaissance avancée**
   - Phishing ciblé pour accéder à des comptes sensibles.
   - Exploitation de bases de fuites de données pour collecter des informations précieuses.

2. **Compromission des systèmes**
   - Utilisation de logiciels malveillants spécifiques pour s'infiltrer dans le réseau.
   - Maintien de la présence avec des outils d’accès à distance sophistiqués et difficiles à détecter.

3. **Exfiltration des données**
   - Volume important de données copiées et exfiltrées, près de 300 Go.
   - Publication des données via des plateformes publiques pour déstabiliser la campagne.

4. **Impact**
   - Déstabilisation politique : réduction de la confiance dans le processus électoral.
   - Favorisation d’un candidat en discréditant l'autre.

Les données analysées montrent un degré élevé de préparation et de coordination dans les activités d’APT28, renforçant leur attribution au GRU.

---

## Discussion des défis rencontrés

L’analyse de ce cas soulève plusieurs défis majeurs :

1. **Attribution** :
   - Identifier avec certitude les auteurs des attaques malgré l’utilisation de techniques de dissimulation sophistiquées.
   - Différencier les activités d’APT28 et d’APT29, souvent imbriquées.

2. **Réponse adaptée** :
   - Mettre en place des mesures de réponse efficaces face à des attaques persistantes sans perturber les opérations du DNC.
   - Gérer les conséquences médiatiques et politiques des fuites de données.

3. **Détection précoce** :
   - Les systèmes de détection en place n’ont pas permis d’identifier les activités malveillantes avant que des volumes massifs de données soient exfiltrés.
   - La faible sensibilisation des employés à la cybersécurité a facilité les campagnes de phishing.

Ces défis illustrent la complexité des attaques ciblant des organisations d’importance critique et soulignent la nécessité d’améliorer les stratégies de défense et de réponse.

---

## Conclusions

Le cas du DNC illustre les capacités évolutives d'APT28, notamment dans sa stratégie de compromission discrète et ses tactiques de déstabilisation politique à grande échelle. Il met en évidence les conséquences directes de campagnes de cyberespionnage ciblé sur des institutions d’importance critique.

Pour prévenir ce type d’attaques, il est essentiel de :
- Renforcer la surveillance des infrastructures critiques.
- Sensibiliser les équipes aux risques de phishing.
- Implémenter des mécanismes de détection avancés contre les activités malveillantes persistantes.

---

## References

1. [Article sur le contenu du Leak du DNC de 2016](https://edition.cnn.com/2016/07/24/politics/dnc-email-leak-wikileaks/index.html)
2. [CrowdStrike et le DNC](https://www.crowdstrike.com/en-us/blog/bears-midst-intrusion-democratic-national-committee/)
3. [Rapport du sénat des États-Unis](https://www.intelligence.senate.gov/sites/default/files/documents/Report_Volume1.pdf)
4. [Comité de renseignement américain, 21 juin 2017](https://www.intelligence.senate.gov/hearings/open-hearing-russian-interference-2016-us-elections)