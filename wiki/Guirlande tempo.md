## main.c
```c
#include <hidef.h>
#include "derivative.h"
#include "header.h"

void main(void){
	unsigned char i;
	
	/* Internal clock of 8MHz selected. */
	ICSC2 = 0x00;
	ICSC1 = 0x04;
	
	/* Disable Watchdog */
	SOPT1_COPE=0; 

	PTBDD = 0xFF;
	for(;;){
		PTBD=0x01;
		for(i=0;i<8;i++){
			tempo(2,51856); //500ms
			PTBD = PTBD << 1;
		}
	}
}
```

## tempo.c
![[Procédure temporisation]]

## Header.h
```c
void tempo(unsigned char nb_boucle,unsigned int taille);
```

D'aprés les calculs, pour la fonction tempo, il faut 2 tour de boucle complète et une autre boucle de 52040.

## Méthode:
**Prérequis**: 
- La **durée** d'un cycle (8MHz).
- Le **nombre** de cycle de la boucle complète.

1) On trouve la durée de la boucle complète en multipliant la durée d'un cycle et le nombre de cycle de la boucle complète. 
2) On peut donc savoir le nombre de boucle complète maximale.
3) Il reste donc un reste de temps. On trouve le nombre de cycle qu'il faut pour le temps restant grâce à un produit en croix
	1->1,25.10^-7 s
	? -> temps restant
4) Grâce à le fonction on trouve le nombre d'itération. 

