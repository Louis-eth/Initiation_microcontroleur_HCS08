## Définition
**TPMSC (Timer Pulse-Width Modulation Status and Control):** Registre permettant de paramétrer l’horloge utilisée et d’autoriser l’interruption sur le timer.

## Documentation
![[Pasted image 20230414121925.png]]
>[!INFO]
>Il est donc indispensable de remettre le bit TOF de TPMSC à 0 à la fin de l'interruption pour que celle-ci puisse prendre fin.
