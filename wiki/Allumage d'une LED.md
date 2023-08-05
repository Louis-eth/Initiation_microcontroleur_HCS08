```c
#include <hidef.h> // for EnableInterrupts macro 
#include "derivative.h" //include peripheral declarations 

void main(void){

	PTBDD = 0xFF; //sortie donc toutes les broches à 1
	PTBD_PTBD0 = 1; // on allume la LED 0

	for(;;){
	}
}
```
