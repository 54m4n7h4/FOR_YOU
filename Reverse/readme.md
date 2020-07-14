# Find Me Friend

L'executable est de type ELF


![](w.png?raw=true)


> ELF (Executable and Linkable Format, format exécutable et liable ; anciennement Executable and Linking Format) est un format de fichier binaire utilisé pour l'enregistrement de code compilé (objets, exécutables, bibliothèques de fonctions). Il a été développé par l’USL (Unix System Laboratories) pour remplacer les anciens formats a.out et COFF qui avaient atteint leurs limites. Aujourd'hui, ce format est utilisé dans la plupart des systèmes d'exploitation de type Unix (GNU/Linux, Solaris, IRIX, System V, BSD), à l'exception de Mac OS X. 


On l'execute et puis le programme nous chasse avec insulte.

ça me met en colère !

Quelle galère !

C'est vraiment misère !



![](exe.png?raw=true)

On retoune sur radare pour le niquer.

# Renversement de la situation

On lance l'exécutable en mode débogage sur radare2 avec la commande : 

```bash
  r2 -d Find_me.exe

```

Analyser tout les symboles et on affiche tous les fonctions aussi avec les commandes suivantes :

```bash
    aaa

```


![](aaa_afl.png?raw=true)


Analysons le code assembleur du main

On utilise la commande :

```bash
    pdf@main

```

![](main.png?raw=true)


On a la fonction sym.l37_m3_h3r3 qui attire l'attention


![](mainf.png?raw=true)


On le désassemble alors avec la commande :

```bash
    pdf@sym.l37_m3_h3r3

```


![](l37_m3_h3r3.png?raw=true)

On a comme ça un truc de malade.

On a quatre chaînes en hexadécimale qui sont interèssant.

```bash

0x464c41477b ; '{GALF
0x48415050595f ; '_YPPAH'
0x4249525448444159 ; 'YADHTRIB'
0x5f4249424c49537d ; '}SILBIB_'

```
Pour trouver le flag il faut juste utiliser xxd sous linux


```bash

xxd -r -p <<<"0x464c41477b"
xxd -r -p <<<"0x48415050595f"
xxd -r -p <<<"0x4249525448444159"
xxd -r -p <<<"0x5f4249424c49537d"
        
        OU
 xxd -r -p <<<"0x464c41477b" ;xxd -r -p <<<"0x48415050595f";xxd -r -p <<<"0x4249525448444159";xxd -r -p <<<"0x5f4249424c49537d"
```

FLAG{HAPPY_BIRTHDAY_BIBLIS}

On a enfin niquer le programme
