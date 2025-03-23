# Context

Comme d'hab, je créer des repos avec pas grand chose dedans, mais là c'est pour approfondir mes compétences DevOps. J'voulais m'essayer un peu à kubernetes, j'ai essayé en local, mais je me disais que ça serait quand même plus amusant si c'était sur un VPS. *Puis parce que le Raspberry Pi 3B+ a pas trop aimé docker XD*

*Les notes qui vont suivrent n'ont pas forcément beaucoup de sens, c'est juste le fruit de mes réflexions, les ressources que j'ai utilisés pour apprendre,...*

## Objectifs

- Funkwhale
- Jupyter notebook

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

``kubectl logs <pod name>``

``kubectl rollout restart <resource type> <name>`` pour redémarrer une ressource. Pratique après un changement de config.

Minikube c'est un peu lourd et compliqué, j'ai préféré installer k3s.

## DNS

Les nom de domaines des services ont la forme ``<service>.<namespace>.svc.cluster.local``. Exemple: ``prometheus-cluster-ip.grafana.svc.cluster.local``

# Helm

Helm est un gestionnaire de paquet pour kubernetes. Un paquet s'appel un charts.

```bash
$ helm repo add stable https://charts.helm.sh/stable
$ helm search repo stable

$ helm repo update # Met à jour la liste des charts.
$ helm install stable/mysql --generate-name

$ helm show chart stable/mysql
$ helm show all stable/mysql

$ helm ls
$ helm list
$ helm status <name>
$ helm uninstall <name>
```