![[Pasted image 20230411183852.png]]
Le mot-clé "extern" en C est utilisé pour déclarer une variable ou une fonction qui a été définie dans un autre fichier source. Lorsqu'une variable ou une fonction est déclarée "extern", cela signifie que son emplacement mémoire est défini dans un autre fichier source et que le compilateur doit chercher cette définition pendant la compilation. Cela permet de partager des variables ou des fonctions entre différents fichiers source d'un projet.

Voici un exemple d'utilisation du mot-clé "extern" pour une variable déclarée dans un autre fichier source :

```c
// fichier1.c 
int myVar = 42;  
// fichier2.c 
extern int myVar;  
int main() {   
	printf("%d\n", myVar);   
	return 0; 
}
```

Dans cet exemple, la variable "myVar" est définie dans le fichier1.c et déclarée comme "extern" dans le fichier2.c. Lorsque le code est compilé, le compilateur utilise la définition de "myVar" dans le fichier1.c pour résoudre la référence dans le fichier2.c.


Le mot-clé "volatile" en C est utilisé pour indiquer que la valeur d'une variable peut être modifiée par des éléments externes au programme, tels que des interruptions ou des périphériques d'E/S.