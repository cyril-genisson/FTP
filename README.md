# FILE TRANSFER PROTOCOL
Pour ce qui est de la question posée en introduction et bien j'ai envie de dire
que je ne passerai pas par un serveur FTP pour transférer des
fichiers d'un ordinateur à un autre en toute sécurité.

En effet l'ensemble des flux réseaux n'est pas crypté...
Au mieux on utiliserait sFTP...

# Job 1 à 5
Les contraintes:
Deux réseaux:
- 192.168.1.0/24
- 172.16.1.0/16

matériel: 2 switchs, 1 routeur, 1 serveur FTP, des postes clients sur les deux réseaux

Configurer un serveur FTP sur le serveur afin de permettre le transfert entre deux
machines

Créer un fichier **mon_test.txt** sur CISCO et y ajouter le texte de notre choix
Transférer un fichier d'un PC du réseau 192.168.1.0 vers un PC du réseau 172.16.1.0
et vice versa pour vérifier que le serveur fonctionnne.



Voir la configuration CISCO dans le fichier FTP.ptk

# Job 6 à 10
Pour ces différents Jobs, on doit donc en résumé:
- installer un serveur Debian sans interface graphique avec un serveur SSH
- installer un serveur FTP: proFTPd
- lancer le serveur
- Ajouter deux utilisateurs:
    - Merry     mot de passe! kalimac
    - Pippin    mot de passe: secondbreakfast
- sur l'hôte créer un fichier **mon_fichier.txt** et le transférer vers la VM Debian

Commençons par le commencement!

## Installation d'une VM Debian
Comme à notre habitude nous utiliserons la virtualisation KVM pour virtualiser notre machine.
Pour plus de détail sur son utlisation, j'invite le lecteur à lire ou relire  l'excellente 
documentation (et ce propos n'engage pas que moi ;-p ) [Hyperception](https://github.com/cyril-genisson/Hyperception/blob/main/Documentation-hyperception-GENISSON.pdf).

Puisque notre machine a peu de besoins pour la démonstration nous utiliserons les paramètres suivants:
- CPU: 2
- Mémoire: 2048Mio
- Image disque 10 Gio
- Réseau routé: Configuration IPv4 192.168.100.0/24

Paramètres d'installation:
- Nom de machine: wolf
- domaine: laplateforme.lan
- Le compte root est vérouillé
- User: kaman Password: xxxxxxxx (Appartient au groupe SUDO)
- Partitionnement:
    - 1 primaire 9.7GB / ext4
    - 5 logique 1.0GB swap swap
- Paquetage: configuration minimale

