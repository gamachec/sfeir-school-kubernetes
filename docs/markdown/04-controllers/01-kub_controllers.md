## Les controllers > **kube-controller-manager**

Les controllers sont des composants essentiels qui appliquent l’état désiré dans le cluster en utilisant une boucle de reconciliation.  
Dans un cluster vierge, les principaux controllers sont regroupés dans le pod **kube-controller-manager**, qui regroupe les controllers suivants :
* **Deployment Controller:** Gère les ReplicaSets et assure la bonne mise à jour des Pods
* **StatefulSet Controller:** Gée des Pods avec état (utilisé pour les bases de données, etc.)
* **DaemonSet Controller:** Assure qu'un Pod s'exécute sur tous les nodes
* **Job Controller:** Lance des Pods pour exécuter des tâches uniques
* **Node Controller:** Surveille les Nodes, détecte les états de santé dégradés
* **Namespace Controller:** Gére la suppression récursive des objets dans un namespace
* **...**