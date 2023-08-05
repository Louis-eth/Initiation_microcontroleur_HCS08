Le timer est simplement réalisé grâce à un compteur qui compte les fronts montants d’un signal d’horloge (éventuellement prédivisé avant d’arriver sur le port d’horloge du compteur). Ceci permet de mesurer un nombre de cycles (entre deux fronts montants) et donc de mesurer un temps de manière assez précise.

![[Pasted image 20230414115910.png]]
Le compteur est incrémenté à chaque front montant du signal d'horloge clk2 indépendamment du
travail du CPU. La valeur de compteur, stockée dans le registre [[TPMCNT]], obtenue en sortie du compteur est comparée à la valeur contenue dans le registre [[TPMMOD]] grâce au comparateur.

Si les deux valeurs sont identiques, le comparateur envoie deux informations :
- un signal reset au compteur qui permet de le remettre à 0 ;
- un signal d'interruption avec niveau de priorité 7 au processeur.

Sinon, le compteur continue à compter à chaque nouveau front montant du signal clk2.