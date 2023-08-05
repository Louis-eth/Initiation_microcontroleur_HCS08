## Code
```c
#include <hidef.h>
#include "derivative.h" 

void main(void) { 
	unsigned int i; 
	
	//Clock de 8MHz 
	ICSC2 = 0x00; 
	ICSC1 = 0x04; 
	
	SOPT1_COPE=0; //Watchdog désactivé
	
	PTBDD=0xFF; //PTB sortie
	
	for(;;) { 
		i=0; 
		while(i<65535) { 
			i++; 
		}//Boucle complète 
	PTBD=~PTBD; // ~ : négation (NOT)
	} 
}
```

## Démonstration
![[20230412-1538-00.3468496.mp4]]
On voit bien sur la vidéo que la valeur à l'adresse 0x0002 change de 0x00 à 0xFF. L'adresse 0x0002 correspond à [[PTBD]]. 

## Durée de la boucle 
On note le nombre de cycle CPU avant et après la boucle: 
![[Pasted image 20230412175018.png]]
On obtient 1 377 269 cycle CPU.

D'après le code la fréquence de l'horloge interne (clock) est de 8MHz. 
D'après la formule: $$f=\frac{1}{T}\Rightarrow T=\frac{1}{f}$$ Donc comme $f=8*10^6$, $T=1,25*10^{-7}s$ 
Un tour d'horloge dure T secondes.
Donc $1,25*10^{-7} * 1 377 269 = 0,17s$ 

**Conclusion: La boucle dure 170ms.**

>[!warning]
>**Pas de proportionnalité entre le nombre de cycles CPU et le nombre d’itérations POUR 2 TYPES DIFFERENTS** parce qu’il faut plus de temps pour le microprocesseur d’ajouter 1 à un unsigned long int qu’à un unsigned int.

## Avoir une boucle qui dure 500ms
Il y a proportionnalité entre le nombre de cycle CPU et le nombre d'itérations seulement pour 2 même type. 
Or pour 500ms: 
$$\frac{65535*500}{170}=192 750$$
Il faut donc 192 750 sauf que 192 750>65 535 il faut donc utiliser un autre type car il n'y a pas de proportionnalité.

### Une solution 
Diviser le nombre de cycle d'horloge grâce à [[ICSC2]]. On choisit de diviser par 4.
La boucle avec 65535 itérations va donc mettre 680ms. Et pour une boucle qui dure 500 ms on va avoir 48 188 itérations (produit en croix).

- Inconvénient: 4* plus lent 