# Less Used

Ici il s'agit d'un fichier pcapng.
Une capture du trafic réseau.
On l'ouvre avec wireshark

Avec wireshark ,dans Statistique->Hiérachie des protocoles on voit les protocole IP suivants : UDP,TCP,ICMP
Il y a aussi le ARP

On commence par le UDP puisque le UDP est moins utilisé que le TCP .

Ici c'est le hint qui nous oriente.

On filtre le trafic pour le UDP uniquement.

On trie en fonction du taille (Du plus pétit au plus grand) dans Length mais ce n'est pas obligatoire.

On voit maintenant qu'il y a autant de requête DNS ,un peu de udp basique,du très peu du DHCP dans ce filtre.

En jettant un coup d'oeil sur les requêtes DNS ça ne donne rien .
On saute sur le datagram UPD basique.

On fait un clic droit sur le premier paquet de taille 27 puis Suivre->Flux UDP

Et baOund !

On a le flag

![](w.png?raw=true)

FLAG{HAPPY_BIRTHDAY_BIBLIS}
