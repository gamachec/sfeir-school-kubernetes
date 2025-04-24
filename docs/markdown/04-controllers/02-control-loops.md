<!-- .slide: class="two-column" -->
## Les controllers > **les boucles de reconciliation**

Qu’est-ce qu’une boucle de reconciliation ?
* Les boucles du Kube-controller-manager observent l’état actuel
* Le compare à l’état désiré
* Agit pour réconcilier les deux.
Cette logique est appelée une boucle de reconciliation.
<br><br>

 3 Pods requis, mais qu’un crash, le controller recrée automatiquement le pod manquant.
<!-- .element: class="admonition custom" data-admonition-icon="🖥️ Exemple" style="--admonition-bg-color:#0bb57f;" -->

##--##

<br><br><br><br>

![center h-550](./assets/images/control-loop.png)

##==##

## Les controllers > **les boucles de reconciliation**

Dans les controllers, les boucles sont lancées de différentes manières : 
* **Périodicité :** Les contrôleurs s'exécutent à intervalles réguliers (configurable)
* **Événements :** Déclenchement sur des événements spécifiques (watch API Server)
* **Backoff exponentiel :** En cas d'erreurs répétées, l'intervalle entre les tentatives augmente  

Il existe des controllers / opérateurs, destinés a étendre l'api kubernetes, embarquants chacuns des boucles de reconciliation  

nginx-ingress-controller<br>
grafana-operator
<!-- .element: class="admonition custom" data-admonition-icon="🖥️ Exemple" style="--admonition-bg-color:#0bb57f;" -->
