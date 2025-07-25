<!-- .slide: class="two-column" -->

## Le cluster Kubernetes > **Vue d'ensemble**

![w-800](./assets/images/archi-kube.png)

##--##

<br><br><br>

Un cluster Kubernetes est composé à minima d'un control plane, et d'un worker node. Afin de conserver de la haute disponibilité, les workers nodes sont souvent au nombre de trois.
* **Control plane** : Il a pour rôle de maintenir l'état souhaité du cluster, en redémarrant des pods, ou en augmentant le nombre de réplica.
* **Worker node** : Ils ont pour rôle d'héberger les applications et d'être joignables de l'exterieur.

Notes:
Un cluster est un ensemble de machines qui collaborent entre elles.

Sur Kubernetes, on distingue le master des nœuds (nodes).

##==##

<!-- .slide: class="two-column" -->

## Le cluster Kubernetes > **Le control plane**

![w-700](./assets/images/kube-control-plane.png)

##--##

<br>

Le control plane a pour but de maintenir l'état désiré du cluster, en étant responsable de l'orchestration. Il posséde les composants suivants :
* **kube-apiserver:**  Valide et traite les requêtes, gere l'authentification et permet aux nodes de connaitre l'état du cluster.
* **etcd:** Base de données de type clef / valeur, stockant l'état du cluster. C'est la source de vérité.
* **kube-scheduler:** Quand un pod n'est pas encore lancé, il regarde les ressources des nodes et selectionne la meilleure.
* **kube-controller-manager:** Gère tous les controllers du cluster.

Notes:
* Le master est responsable de d’essentiel de la partie “contrôle” (control plane) du cluster.
* Les nœuds (nodes) sont responsables de l’exécution des applications.
* Expliquer ce qu'est un controler kube (boucle de réconciliation)

##==##

<!-- .slide: class="two-column" -->

## Le cluster Kubernetes > **Le worker node**

![w-700](./assets/images/kube-worker-node.png)

##--##

<br>

Le worker node a pour but de permettre aux pods applicatifs d'être démarrés grâce à une communication avec le control plane. Il posséde les composants suivants :
* **kubelet:** Agent qui execute les pods en suivant les specs des ressources demandées par l'api server.
* **kube-proxy:** Agent de gestion du réseau pour les pods au travers des services. C'est un proxy UDP/TCP.
* **container-runtime:** Agent responsable du pull des images, de lancer les conteneurs et leur allouer des ressources.

Notes:
* Les nœeuds exécutent les applications packagées dans des containers regroupés dans des “Pods”.

* L’exécution des Pods est gérée par les kubelet.

Kubelet est un process qui pilote le moteur de containeurs
respectant le CRI (Container Runtime Interface)
ex:
(Docker engines, CRI-O, Containerd)

* Les fonctions de master et de node sont habituellement déployées sur des machines différentes.
* En dev les master et workers peuvent être déployées sur une unique machine (ex: Minikube)

##==##

<!-- .slide:-->

<!-- .slide: class="two-column" -->

## Le cluster Kubernetes > **Les pods**

![w-800](./assets/images/kube-pods.png)

##--##

<br><br><br>

C'est la plus petite ressource déployable sur Kubernetes, contenant un ou plusieurs conteneurs partageant le réseau et le stockage.
* **Réseau:** L'ensemble des conteneurs dans un pod partagent la même adresse IP.
* **Cycle de vie:** Tous les conteneurs d'un pod sont créés et détruits ensemble.
* **Gestion:** Généralement, ils sont gérés par des controllers de plus haut niveau (déploiement, statefulset ou daemonset).

Notes:
Pod :
1 ou plusieurs containers
en général un seul
partageant :
une seule IP
un ou plusieurs volumes

##==##

<!-- .slide:-->

## Le cluster Kubernetes > **Les composants additionnels: DNS**

![center h-600](./assets/images/kube-dns.png)

* Le dns interne est `core-dns` remplacant de `kube-dns` depuis la version 1.11 en juillet 2018.
  * les requetes dns utilisent core dns pour connaitre les noms des services internes, et le `resolv.conf` de la machine hôte pour les noms externes.

##==##

<!-- .slide:-->

## Le cluster Kubernetes > **Les composants additionnels: CNI (Container Network Interface)**

![center h-700](./assets/images/kube-cni.png)

Notes:
* CNI est une spécification qui standardise la gestion du réseau pour les conteneurs.
* Permet à Kubernetes de connecter les pods entre eux et au reste du réseau.
* Les plugins CNI ajoutent, configurent et suppriment les interfaces réseau des pods.

Deux CNI populaires :
* Flannel (vlan) = simplicité, connectivité de base.
* Calico (mode "routé) = performance, sécurité, fonctionnalités avancées.
* CNI spécifiques pour les gros providers (AWS, Google, ...)

##==##

<!-- .slide:-->

## Le cluster Kubernetes > **Les composants additionnels: CSI (Container Storage Interface)**

![center h-500](./assets/images/kube-csi.png)


Pas de CSI installé sur le cluster à l'initialisation celui-ci étant dépendant du storage provider.  
<!-- .element: class="admonition warning" -->

Notes:
* Permet à Kubernetes de se connecter à différents systèmes de stockage (disques locaux, SAN, cloud, etc.).
* Les plugins CSI créent, attachent, détachent et suppriment des volumes pour les pods.
* Grâce à CSI, Kubernetes peut intégrer facilement de nouveaux fournisseurs de stockage, sans modification du cœur du système.
* En résumé: CSI rend le stockage flexible et extensible pour les applications dans Kubernetes.

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel composant du Control Plane est responsable de la prise de décisions concernant le placement des pods sur les nœuds ?
* kube-apiserver
* etcd
* kube-scheduler
* kubelet

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel composant du Control Plane est responsable de la prise de décisions concernant le placement des pods sur les nœuds ?
* kube-apiserver
* etcd
* **kube-scheduler**
* kubelet

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel composant stocke l'état et la configuration de l'ensemble du cluster Kubernetes ?
* kube-controller-manager
* etcd
* kube-proxy
* coredns

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel composant stocke l'état et la configuration de l'ensemble du cluster Kubernetes ?
* kube-controller-manager
* **etcd**
* kube-proxy
* coredns

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel agent s'exécute sur chaque nœud et est responsable de la communication avec le Control Plane pour s'assurer que les conteneurs fonctionnent dans un pod ?
* kube-proxy
* container runtime
* kubelet
* kube-scheduler

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel agent s'exécute sur chaque nœud et est responsable de la communication avec le Control Plane pour s'assurer que les conteneurs fonctionnent dans un pod ?
* kube-proxy
* container runtime
* **kubelet**
* kube-scheduler

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel composant est responsable de la gestion des règles réseau et de l'équilibrage de charge pour les services Kubernetes ?
* kubelet
* kube-proxy
* coredns
* kube-controller-manager

##==##

<!-- .slide: class="exercice" -->
## Quiz

Quel composant est responsable de la gestion des règles réseau et de l'équilibrage de charge pour les services Kubernetes ?
* kubelet
* **kube-proxy**
* coredns
* kube-controller-manager
