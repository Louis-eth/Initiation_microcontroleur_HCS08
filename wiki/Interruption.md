```c
void interrupt 7 Depassement_compteur(void){ 
	/*On interrompt le processeur pour faire quelque chose*/ 
	/*Ce quelque chose se traduit par des instructions à traiter pendant l’interruption qu’il faut positionner ici*/ 
//Attention à bien remettre à 0 le bit TOF après avoir traitée les instructions de l’interruption 
TPMSC=TPMSC & 0b01111111; 
}//fin de l’interruption
```