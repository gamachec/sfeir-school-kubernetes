<!-- .slide:-->

## Introduction > **Produit Open-source**
![float-left h-300](./assets/images/K8S-logo.png)
* <https://github.com/kubernetes/kubernetes>

  * **116k+** stars
  * **3.8k+** contributeurs
* Premier projet intégré à la création de la CNCF en Juillet 2015

Notes:
- CNCF: Cloud Native Computing Foundation

##==##
## Introduction > **Cloud Native Computing Foundation**
![](./assets/images/cncf-orchestrator.png)
<div style="text-align: center">
  <a href="https://landscape.cncf.io" target="_blank">landscape.cncf.io</a>
</div>  

* Fondée en 2015, c'est une organisation à but non lucratif, ayant pour mission de favoriser l'adoption des technologies tournant autour du Cloud.
  * heberge de nombreux projets open source
  * organise des evenements (kubecon)
  * propose des certifications

Notes:
* Fait partie de la Linux Foundation.
* Gouvernée par un comité directeur composé de membres issus de grandes entreprises du secteur (Google, Microsoft, IBM, etc.) et de la communauté open source.

* Incubating : projets en cours de développement, prometteurs mais pas encore totalement matures. Ils sont activement développés et évalués.
* Graduated : projets matures, largement adoptés, avec une communauté active et des pratiques de sécurité et de gouvernance éprouvées.



##==##
## Introduction > **Apercu**
![center h-800](./assets/images/archi-kube.png)

<!-- .element: class="credits" -->

Notes:
* Kubernetes = barreur d'un navire en grec
* Abrégé en K8S = k..8 lettres..s
* écrit en Go par Google

* "Cluster Kubernetes" = des noeuds maîtres & des workers
Parler à minima des pods pour permettre de répondre à la question du quizz


##==##
## Introduction > **Les versions (semver)**
Pour nommer ses versions, Kubernetes utilise du semantic versioning (x.y.z)
* *x* est le numéro de la version **majeure**
* *y* est l'incrément de la version **mineure**
* *z* est le niveau de **correctif**

Lors de montée de version, l'api de kubernetes est enrichie, et rares sont les endpoints qui sont supprimés. Une montée de version est donc rarement risquée.
* La version 1.33 est la dernière en date (15/05/2025)
* Une version mineur sort tous les 4 mois.
* Si une api devient dépréciée, elle est retirée au bout d'un an (soit 4 versions plus tard).

##==##


<!-- .slide: class="two-column" -->
## Introduction > **Kubernetes, pour quoi faire ?**

![w-600](./assets/images/kub-for-what.svg)

##--##

<br><br>

- **Orchestration automatisée** : Peu d'actions manuelles.
- **Haute disponibilité** : Répartition de charge et relance automatique.
- **Scalabilité** : Possibilité de faire du scaling automatique.
- **Portabilité** : Déploiement quasi identique entre on premise et les différents cloud.
- **Gestion déclarative** : Avoir l'ensemble de ses déploiements as code.
- **Écosystème riche** : Énormément d'outils/extensions et communauté active.

Notes:

##==##

<!-- .slide: class="exercice" -->

## Quiz

<br>

_Question_ : Dans quel langage est développé Kubernetes ?

<br>

1. C++
2. Java
3. Golang
4. PHP

##==##

<!-- .slide: class="exercice" -->

## Quiz

<br>

_Question_ : Dans quel langage est développé Kubernetes ?

<br>

1. C++
2. Java
3. **Golang**
4. PHP

##==##
<!-- .slide: class="exercice" -->
## Quiz

<br>

_Question_ : Quel est le rôle principal d'un "Pod" dans Kubernetes ?

<br>

1. Stocker des données persistantes
2. Exécuter un ou plusieurs conteneurs
3. Gérer le réseau du cluster
4. Orchestrer les déploiements

##==##

<!-- .slide: class="exercice" -->

## Quiz

<br>

_Question_ : Quel est le rôle principal d'un "Pod" dans Kubernetes ?

<br>

1. Stocker des données persistantes
2. **Exécuter un ou plusieurs conteneurs**
3. Gérer le réseau du cluster
4. Orchestrer les déploiements
