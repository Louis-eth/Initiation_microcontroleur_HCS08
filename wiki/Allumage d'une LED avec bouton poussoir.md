## main.c
```c
#include <hidef.h> // for EnableInterrupts macro 
#include "derivative.h" //include peripheral declarations 
#include "header.h"

void main(void){
	PTBDD = 0xFF; //sortie donc toutes les broches à 1
	PTADD_PTADD = 0x00; //voir doc PTADD (que les 6 premiers bits) entrée donc 0
	
	for(;;){
		if(BP){
			PTBD = 0xFF; //bouton pressé
		}
		else{
			PTBD = 0x00;//bouton non pressé
		}
	}
}
```

## header.h
```c
#define BP !PTAD_PTAD1 
```
