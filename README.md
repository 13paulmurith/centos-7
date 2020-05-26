# Script de configuration post-installation pour les serveurs CentOS 7 

(c) Niki Kovacs, 2020

Ce référentiel fournit un script "automatique" de configuration post-installation pour des serveurs fonctionnant sous CentOS 7 ainsi qu'une collection de scripts d'aide et des modèles de fichiers de configurations pour les services communs.

## En bref

Effectuez les étapes suivantes.

  1. Installez un système CentOS 7 minimum.

  2. Créez un utilisateur non "root" avec des privilèges d'administrateur.

  3. Installez Git : sudo yum install git

  4. Clonez le dépôt git : `git clone https://gitlab.com/kikinovak/centos-7.git`

  5. Déplacez vous vers le nouveau répertoire : "cd centos-7".

  6. Exécutez le script : sudo ./centos-setup.sh --setup

  7. Prenez une tasse de café pendant que le script fait tout le travail.

  8. Redémarrez.

## Personnalisation d'un serveur CentOS

Transformez une installation CentOS minimale en un serveur fonctionnel abouti toujours à une série d'opérations plus ou moins longues. La durée peut varier bien sûr, mais voici ce que je fais habituellement sur une nouvelle installation CentOS :

  * Personnaliser le shell Bash : prompt, alias, etc.

  * Personnaliser l'éditeur Vim.

  * Installation des dépôts officiels et tiers.

  * Installer un ensemble complet d'outils en ligne de commande.

  * Supprimer les paquets inutiles.

  * Permettre à l'utilisateur administrateur d'accéder aux journaux du système.

  * Désactiver l'IPv6 et reconfigurer certains services en conséquence.
  
  * Configurer un mot de passe persistant pour `sudo`.

  * Etc.

Le script `centos-setup.sh` effectue toutes ces opérations.

Configurez Bash et Vim et définissez une résolution de console par défaut plus lisible :

```
# ./centos-setup.sh --shell
```

Mettre en place les dépôts officiels et les dépôts de tiers :

```
# ./centos-setup.sh --repos
```

Installez les groupes de paquets `Core` et `Base` ainsi que quelques outils supplémentaires :

```
# ./centos-setup.sh --extra
```

Retirez les paquets inutiles :

```
# ./centos-setup.sh --prune
```

Permettre à l'utilisateur administrateur d'accéder aux journaux du système :

```
# ./centos-setup.sh --logs
```

Désactivez l'IPv6 et reconfigurez les services de base en conséquence :

```
# ./centos-setup.sh --ipv4
```

Configurez la persistance du mot de passe pour sudo :

```
# ./centos-setup.sh --sudo
```

Réalisez tout cela en une seule fois :

```
# ./centos-setup.sh --setup
```

Enlevez les paquets et revenir à un système de base amélioré :

```
# ./centos-setup.sh --strip
```

Affichez le message d'aide :

```
# ./centos-setup.sh --help
```

Si vous voulez savoir ce qui se passe exactement sur le serveur, ouvrez un deuxième terminal et consultez les journaux :

```
$ tail -f /tmp/centos-setup.log
```

