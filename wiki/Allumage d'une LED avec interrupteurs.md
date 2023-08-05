## main.c
```c
#include <hidef.h> /* for EnableInterrupts macro */
#include "derivative.h" /* include peripheral declarations */

void main(void) {
	PTBDD = 0xFF; //sortie donc toutes les broches à 1
	PTBD = 0x00;//on éteint toutes les LEDs
	
	PTADD_PTADD = 0x00; //entrée donc 0

  for(;;) {
   	if(SW1 && SW2))
  	{
  		PTBD=0xFF;	
  	}
  	else
  	{
  		PTBD=0x00;
  	}
  }
}

```

## header.h
```c
#define SW1 !PTAD_PTAD2
#define SW2 !PTAD_PTAD3
```
