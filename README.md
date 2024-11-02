# Kubernetes Learning

Après des heures à tenter de créer une vm dans wsl avec kvm, les problèmes engendrés, je fini par lancer le driver en mode docker, parce que j'avais pas compris comment ça allait se faire avant. En fait on peut utiliser docker comme "hyperviseur", permettant de ne pas avoir à s'embêter avec du KVM.

Au lieu de taper les commandes pour tout créer, on peut créer des manifests en yaml et faire des kubectl apply. Ca me rappel un peu kafkactl dans cette logique.

- [tuto de la doc](https://kubernetes.io/fr/docs/tutorials/hello-minikube/)
- [Très bon tuto Kubernetes](https://blog.stephane-robert.info/docs/conteneurs/orchestrateurs/kubernetes/introduction/)
- [Comment écrire les manifest](https://blog.stephane-robert.info/docs/conteneurs/orchestrateurs/kubernetes/ecrire-manifests/)

Attention car des fois les commandes d'info ne trouvent pas nos éléments car ils sont dans un namespace. On peut donc rajouter ``-n <namespace>``. Pour tout récup ``kubectl get svc --all-namespaces``


**Pour accéder aux services avec k3s dans wsl, je dois mettre l'ip du wsl récupérable avec ``ip addr show dev eth0``.**
[source](https://gist.github.com/ibuildthecloud/1b7d6940552ada6d37f54c71a89f7d00)

Pour rentrer dans un pod `` kubectl exec -it <POD> -- bash``


[Tuto pour faire un wordpress](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/)

**Faire les tutorials:** [Tutorial](https://kubernetes.io/docs/tutorials/)


Dans les secrets générator, on spécifie les éléments (fichiers) qui ont accès au generator.

La commande describe affiche des morceaux de logs.