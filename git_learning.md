
# Juego "Learn Git Branching"

## Commits de Git

Un commit en un repositorio git registra un snapshot de todos los    
archivos en tu directorio. Es como un gran copy&paste.

Comando
~~~
git commit
~~~

## Ramas en Git

Las ramas (branches) en Git son increíblemente livianas. Son sólo referencias a un   
commit específico - nada más.

Comando
~~~
git branch (nombre_rama)
~~~

## Checkout 

Esto nos situa en una rama para commitear nuestros cambiosen dicha rama.

Comando
~~~
git checkout (nombre_rama)
~~~

## Mergeando ramas

Mergear en Git crea un commit especial que tiene dos padres diferentes. Un commit con    
dos padres esencialmente significa incluir todo el trabajo de este padre de acá y   
este otro padre de acá, y del conjunto de todos sus ancestros.

Comando
~~~
git merge (nombre_rama)
~~~

## Git Rebase

El segundo modo de combinar el trabajo de distintas ramas es el rebase.     
Rebasear esencialmente agarra un conjunto de commits, los "copia", y    
los aplica sobre algún otro lado.

Comando
~~~
git rebase (nombre_rama)
~~~ 

## Referencias relativas

Moverse por git usando los hashes de los commits puede volverse un tanto tedioso.   
En el mundo real no vas a tener una visualización de commits tan linda en la terminal,   
así que vas a tener que usar ` git log ` para ver los hashes.   


### Los commits relativos son poderosos, pero ahora vamos a presentar sólo dos formas simples:  

Moverse un commit atrás con (equivalente a "el primer padre de main".):  

~~~
git checkout main^
~~~

Moverse una cantidad de commits atrás con:

~~~
git checkout main~6
~~~

## Forzando los branches

Una de las formas más comunes en que uso las referencias relativas es para mover las ramas.   
Podés reasignar directamente una rama a un commit usando la opción ` -f `. Así que algo como:  

Comando 
~~~
git branch -f main HEAD~3
~~~
Esto mueve (forzadamente) la rama main tres padres atrás de HEAD.

## Revirtiendo cambios en git

Hay dos formas principales de deshacer cambios en git -- uno es usando ` git reset ` y el otro   
es usando ` git revert `. Vamos a ver cada uno de esos a continuación.

### git reset 

Revierte los cambios moviendo la referencia de una rama hacia atrás en el tiempo   
a un commit anterior.

Comando
~~~
git reset HEAD~1
~~~

### git revert

Revierte cambios y comparte esa revertida con el resto.

Comando
~~~
git revert HEAD
~~~

## Git Cherry-pick

Es una manera directa de copiar una serie de commits sobre tu ubicación actual (HEAD)

Comando 
~~~
git cherry-pick <Commit1> <Commit2> <...>
~~~

## git rebase interactivo

Todo rebase interactivo significa usar el comando ` rebase ` con la opción ` -i `.

Si incluís esta opción, git abrirá una UI para mostrarte qué commits están a punto   
de ser copiados sobre el objetivo del rebase. También muestra sus hashes y mensajes,   
que ayuda mucho para saber qué es cada commit.

Comando 
~~~
git rebase -i HEAD~4
~~~

Esto copiara los commits exactamente como espesificaste

## Tags en git

Manera de marcar permanentemente puntos en la historia de tu proyecto.

Comando
~~~
git tag v1 c1 
~~~

## Git Describe

Como los tags sirven tanto para marcar "hitos" en el código, git tiene   
un comando para describir (describe) dónde estás relativo al "hito" más   
cercano (digamos, "tag"). Y ese comamndo se llama ` git describe `.

Comando
~~~
git describe <ref>
~~~
Donde `<ref>` es cualquier cosa que git puede resolver a un commit.  
Si no especificás ninguna referencia, git simplemente usa el commit   
en que estás parado ahora (`HEAD`).

## Especificando los padres

En lugar de especificar cuántas generaciones hacia atrás ir (como ~), el   
modificador de ^ especifica por cuál de las referencias padres seguir en   
un commit de merge. Recordá que un commit de merge tiene múltiples padres,  
 por lo que el camino a seguir es ambiguo.

Git normalmente sigue el "primer" padre de un commit de merge, pero   
especificando un número junto con ^ cambia este comportamiento predefinido.

Comandos
~~~
git checkout main^         // Subir a la rama padre
git checkout main^2        // Subir a la rama padre 2
git checkout HEAD~^2~2     // Modificadores encadenados
~~~

## git clone

Te permite copiar todo un repositorio a local, con todo y su linea temporal.   
Permitiendote hacer cambios y enviarlos en caso de ser un colaborador.

Comando
~~~
git clone <URL>
~~~

## git fetch

Este comando te permite bajarte los ultimos cambios del codigo sin alterar el   
estado actual del mismo.

Significa que los cambios de tus compañeros no se verán reflejados en tu rama,   
pero si sobre la rama que ellos trabajaron. 

## git pull

baja los cambios y unirlos con tus avances actuales.

Comando
~~~
git pull
~~~

## git push

Envia tus cambios o commits locales al repositorio remoto. Utilizado para su   
posterior merge en la rama principal en caso de que este bloqueada.

Comando
~~~
git push
~~~

## Git fakeTeamwork

Este comando crea un commit en el repositorio remoto simulando un commit de   
algun compañero de equipo.