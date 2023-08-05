## main.c
```c
#include <hidef.h>
#include "derivative.h"
#include "header.h"

void main(void) {
	unsigned char i=0;
	
	/*Autorisation des interruptions */
	EnableInterrupts;

	
	/* Selection horloge interne `a 8MHz */
	ICSC2 = 0x00;
	ICSC1 = 0x04;
	
	/* D´esactivation du Watchdog */
	SOPT1_COPE=0;
	
	/* Initialisation de TPMSC */
	TPMSC=0b01001110;
	
	/* D´efinition de la valeur max de comptage */
	TPMMOD=0xF424;
	
	PTBDD=0xFF;
	PTBD=0x01;
	PTADD=0;

	for(;;) {
		if(PTBD==0x00)
		{
			PTBD=0x01;
		}
	
	} /* loop forever */
}
```

## interruption_timer.c
```c
void interrupt 7 Depassement_compteur(void){
	/*On interrompt le processeur pour faire quelque chose*/
	/*Ce quelque chose se traduit par des instructions `a
	traiter pendant l’interruption qu’il faut positionner ici*/
	//Attention `a bien remettre `a 0 le bit TOF apr`es avoir trait´e les instructions de l’interruption
	
	
	PTBD = PTBD << 1;
	TPMSC=TPMSC & 0b01111111;
	
	
	
}//fin de l’interruption
```
