# Diferencias entre Git Merge y Git Merge --no--ff

Antes de explicar la diferencia entre ambos comandos debemos entender previamente que es el Fast Forward.

## Fast Forward
Git esta enfocado a la eficiencia, debido a esto usa el sistema Fast Forward para unir dos ramas siempre que sea posible. Este sistema primero detecta si es que las ramas a unirse son ancestros directos, esto se produce generalmente cuando no hacemos ningun cambio en la rama principal y solo hacemos cambios en la rama que se separo de esta. 
   
Como git detecta que solo se hicieron cambios en la rama secundaria, lo que hace es simplemente mover el puntero de la rama principal al ultimo commit de la rama que queremos unir.

Si es que git no puede aplicar el Fast Forward debido a que se realizaron cambios en ambas ramas, intentara un proceso recursivo, en el cual creara un nuevo commit, uniendo los archivos de ambas ramas, y moviendo los punteros de ambas a dicho commit.

Si es que Git no puede aplicar un proceso recursivo, (por ejemplo si es que se realizaron cambios en el mismo archivo en ambas ramas), Git nos dira pedira que resolvamos el proceso manualmente, seleccionando aquellos archivos que nosotros consideremos mas relevantes para crear el nuevo commit union de ambas ramas.

## Diferencias
La difernecia es muy simple, si es que aplicamos solo Git Merge, este aplicara el proceso Fast Forward automaticamente, si es que no puede aplicar dicho proceso, pasara al recursivo, o finalmente al manual.

Si aplicamos Git Merge --no--ff le diremos explicitamente a Git que no queremos que aplique el Fast Forward, por lo que Git creara un nuevo commit con los cambios donde apunten ambas ramas (como en el proceso recursivo). Si es que no puede aplicar este comando, tendremos que realizar el proceso manual de seleccion de archivos para el nuevo commit.

En la imagen podemos ver la diferencia entre ambos en una ilustracion, a la izquierda el Git Merge y a la derecha el Git Merge --no--ff.

![Diferencia grafica](https://lh3.googleusercontent.com/proxy/V7WL8HbXbcCkJpgcYauzo5YHTOexURq7FNr8wWpdBIu11vF8GNcKwMbS7ChU2HKazqhw28n4pxAH00VB7x-bLeOcktWutnyjDDSTIpxxn11wYZ6SvwBzr8uUL0MLwQpVS__p)