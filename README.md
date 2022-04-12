# Respaldo-git

## Clases de git

comando para configurar el usuario a utilizar al inicio:
```git config --global user.name "joao ormeño"```

comando para el correo:
git config --global user.email "joao23.1996@gmail.com"

IMPORTANTE: el correo y todo debe ser igual al de la cuenta de github

para listar:
git config --global -e

esc
:wq!

para meterse al repositorio:
cd y link del repositorio

para inicializar el repositorio:
git init

informacion sobre commits:
git status

para agregar todos los archivos a status:
git status *
git status .

commit es una fotografia o punto para poder retroceder o avanzar
git log


para commits 

git commit -m nombrecommit

**********************************

*** COMANDO PARA POSIBLE ERROR DE UN CARACTER O CRLF ***
git config core.autocrlf true

***********************************

para restaurar el ultimo punto commit:
git checkout -- .


comando para indicar en que rama estoy trabajando:
git branch

para cambiar el nombre de una rama:
git branch -m nombreactual nuevonombre

********* °°°°
para cambiar la rama principal:
git config --global init.defaultBranch main
********** °°°°

UNTRACK o U --> no se le esta dando seguimiento al archivo


para ver los commits:
git log

para sacar archivos de seguimiento en git:
git reset nombrearchivo
multiples archivos
git reset nombrearchivo1 nombrearchivo2
(lo mismo para agregar archivos)


para agregar o eliminar archivos especificos de un tipo:
git add *.html
git reset *.html

para ver los archivos de otra carpeta y agregarlos:
git add carpeta/*.tipoarchivo
git add css/ --> añade todo lo de ese directorio

para que git reconozca una carpeta vacia crear archivo
.gitkeep


 informacion de los archivos en la carpeta (resumido al git status)
git status --short


para poder hacer alias de comandos y resumirlos a gusto personal
git config --global alias.aquivaelalias "status --short" (se coloca el comando entre "" sin el git)

para modificar estos alias:
git config --global -e


informacion de commits más corta
git log --oneline


este es un alias que sirve para el git log más corto, detallado y ordenado:
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"

(faltan comillas)
alias de status:
git config --global alias.s status --short
alternativa:
git config --global alias.s status -sb

 
para poder ver las modificaciones:
git diff
para ver los cambios en el stage:
git diff --staged
también se puede jacer por archivo



para crear un commit:
git commit -am nombre
para actualizar un mensaje de commit:
git commit --amend -m "mensaje actualizado"
para meterse en el menu de editor del commit:
git commit --amend

para revertir un commit:
git reset --soft (o --hard que elimina los cambios) HEAD^(colocas un numero para saber que commit quieres sin numero se va al ultimo)


en caso de una advertencia de warning CRLF usar este codigo para omitirla:
git config core.autocrlf true

para ver lo que se a hecho en orden cronologico:
git reflog
para poder reconstruir un commit borrado en el git reflog (con el codigo):
git reset --hard aqui(acá va el codigo del commit)

renombrar commit en git guardado:
git mv nombreactual.archivo nuevonombre.archivo

para remover el archivo de git:
git rm nombrearchivo.archivo

para sacar algún archivo del stage:
git restore --staged archivo



para poder ignorar los archivos se hace un archivo en el proyecto llamado:
.gitignore
dentro de este archivo se anotan los archivos que no quieres que se les haga seguimiento.


preguntar por archivo readme.md
---------------------------------------------------------------------------

Ramas - merges - entre otros.


para crear una nueva rama:
git branch nombre

para ver las ramas:
git branch

para movernos a la rama que queremos:
git checkout nombre

******************************************************************
IMPORTANTE: Para poder mover los cambios a la rama principal debo estar parado en la rama master, de lo contrario los ultimos cambios de la rama master se iran a la rama alternativa
******************************************************************

para fusionar las ramas:
git merge nombre

Dato: si sale fast-forward despues de una fusion es bueno ya que git reconoció todos los cambios añadidos

para borrar una rama después de una fusion:
git branch -d nombre
en caso de detectar datos no añadidos y para borrarlo de manera forzada:
git branch -d nombre -f

para crear la rama e irse de inmediato a ella:
git checkout -b nombre

*************************************************************************
dato: la estrategia RECURSIVA solo lo hace cuando se fusionan de manera automatica y no hay conflictos
dato conflicto: si hay un conflicto solamente remover lo que no necesitamos y dejar lo que queremos en el proyecto, terminando hay que hacer un nuevo commit para guardar los cambios
IMPORTANTE: no trabajar sobre conflicto, resolver el conflicto y ahí podemos seguir expandiendo el programa
*************************************************************************

para crear un tag:
git tag nombre

para borrar el tag:
git tag -d nombre


V1.0.0 primer numero grandes cambios, segundo numero agrega funciones (parches), tercer numero arregla bugs o cosas así.

version anotada tag(requiere de un mensaje):
git tag -a V1.0.0 -m "version 1.0.0 lista"

para colocarle un tag a un commit existente:
git tag -a nombretag codigocommit -m mensaje

para ver los tags:
git tag
para mas detalles del tag y commit:
git show nombretag

----------------------------------------------------------------
stash = caja fuerte para las ramas

comando:
git stash

para tomar el ultimo stash y lo elimina:
git stash pop
(después del stash agregar un commit)

para borrar los stash:
git stash clear

*********************************************************************
Nota: con el git reflog puedes viajar en el tiempo para poder recuperar lo borrado.
*********************************************************************
Información adicional de los stash: https://git-scm.com/docs/git-stash
*********************************************************************
para ver la lista de stash:
git stash list

para recuperar antiguos stash:
git stash apply nombrestash

para borrar un stash especifico:
git stash drop nombrestash

para ver los stash:
git stash show nombrestash

*********************************************************************
Nota: es mejor trabajar con ramas pero se puede hacer algún stash para guardar datos en caso de apuro
*********************************************************************

para guardar un stash con nombre:
git stash save "nombre"

**********************************************************************
NOTA: stash sirve para algo temporal, no para acumular información.
**********************************************************************
**********************************************************************
NOTA: Para hacer un git rebase tienes que estár en la rama que quieres hacer los cambios (master u otros)
*****************************************************************

para actualizar y subir las ramas a la master (o a la que necesite)
git rebase master

*******************************************************************
NOTA: posteriormente te diriges a la rama de trabajo y puedes hacer una fusion de las ramas con la master, para después borrar la rama ya fusionada con el git branch -d nombrerama
*******************************************************************

para poder usar, modificar entre otros el commit de forma interactiva:
git rebase -i HEAD~4 (el numero representa al commit antes del head)

*****************************************************************
Nota: squash se utiliza para unir los commits
*****************************************************************
*****************************************************************
Nota: en el modo rebase el a es para editar
*****************************************************************


para reconstruir todo a como estaba en el ultimo commit>
git checkout -- .  (para restaurar un solo archivo en vez de . colocar nombre del archivo)

***********************************
consultar(consultar por el -m  el -am y --amend):
git commit -m nombrecommit
***********************************


______________________________________________________________________________


GITHUB.com

para subir los tags de un repositorio desde git:
git push --tags

para traer los datos que se encuentran en el origen que está seteado por defecto:
git pull
(para ver la información sirve este comando)
para ver los repositorios donde están alojados:
git remote -v

_______________________________________________________________________________
para unir el repositorio remoto y el local:
git config pull.rebase false  #solo usara el merge
git config pull.rebase true   #rebase
git config pull.ff only	      #fast forward only  (esté es el que buscamos)
_______________________________________________________________________________

esto es para que no vuelva a aparecer el warning:
git config --global pull.ff only
git config --global -e (para apreciarlo)

esc - :q:

***************************************************************************
DATO: con git pull puedes actualizar el repositorio que estas trabajando.
***************************************************************************

para clonar un repositorio desde github debes copiar el link que sale en code y colocar en git:
git clone link


para subir cambios locales al repositorio remoto:
git push
(puede causar conflictos si se hicieron cambios en el repositorio desde github)

en caso de no poder traer los cambios mediante fast forward usar:
git config pull.rebase true

para sacar el rebaseing:
git add . 
git status
git s
git commit -m nombrecommit
git s (no deberia haber nada)
git status (mostrara un menu interactivo)
git rebase --continue

para mantener el pull.rebase true:
git config --global pull.rebase true


para poder clonar un repositorio y colaborar:
primero pinchar en fork para copiar el repositorio de la persona para colaborar.
obtienes el link del repositorio, lo copias y abres git, donde tendrás que meterte al directorio que quieres que esté el repositorio.
por medio de un cd en consola.

git clone link


para poder ver el origen de los repositorios usar:
git remote -v

para poder corregir un commit anterior sin alterar los otros cambios:
git checkout codigocommit nombrearchivo

para poder hacer un fetch and merge, pero no se tendrá la información de ese merge con la rama principal.
pero ahi puedes comparar y ver avances del trabajo con el fetch and merge puedes unir el trabajo al repositorio central.

para traer un repositorio que solo necesito la información se utilizará el upstream:
git remote add nombre(upstream) link

para traer el repositorio original de alguien más (no servirá el git pull)
git pull nombredeupstream nombrerama

el git status siempre te dirá lo que está ocurriendo.

_________________________________________________________________________________
NOTA: recordar que cada vez que se haga algo especial tienes que hacer un commit de lo ocurrido.
_________________________________________________________________________________

NOTA: los forks son trabajos que vienen de un repositorio central, donde los compañeros lo descargan y suben sus avances a su repositorio clonado para posteriormente solicitar la unión al repositorio central.
esto sirve en caso de no dar autorización a alguien para trabajar en el repositorio central.

_________________________________________________________________________________

FLUJO DE TRABAJO

para revisar los trabajos de otros compañeros usar:
git fetch
git branch -a (para revisar las ramas del repositorio)
git checkout rama-capitan

si trabajamos de esta forma cualquier compañero puede hacer un push al repositorio en github
así que estar actualizado el repositorio:

git checkout master
git merge rama-capitan
git push

otras opciones para el mismo trabajo.

git push origin rama-silver
pull request (con esto el equipo sabra los cambios que se han hecho y verlos entre todos)


NOTA IMPORTANTE: descargar los archivos en un formato zip no descargará los commits de los archivos.

para poder mover los cambios hecho a una rama nueva (solo los archivos a los cuales git no les esté haciendo seguimiento)
git checkout -b nombrerama  (esto es para crear la rama y dirigirnos de manera inmediata)
git add .
git commit -m "nombrecommit"
al tirar un git push me salrá error (en el error está el comando que necesitamos) ya que no está la rama en el repositorio main.
para poder subir la rama al repositorio main:
git push --set-upstream origin nombrerama

los cambios apareceran en github para poder hacer una comparación y un pull request

_____________________________________________________________________________________

para configurar alias o comandos abreviados:
git config --global -e

modo edicion y buscamos el alias.

te muestra
git status --short(para ver la información del repositorio ***PROBAR***) --branch (te dice la rama en la que estas)
git status -sb 


en caso de compartir el repositorio y trabajar en equipo. al momento de subir las ramas o hacer ramas desde git puede que no aparezcan.
la solucion para poder verlas después de bajar bajar el repositorio y dejarlo al día es:
git branch -a

para poder bajar todos los cambios desde github:
git pull --all 
git pull (o solo eso)

NOTA: pueden haber conflictos al trabajar 2 personas en la misma rama. dialogar para trabajar en distintos tiempos.

para poder limpiar las ramas que no necesito y que se borraron pero quedaron grabadas como basura:
git remote prune "origin" (el nombre es el repositorio al que se le quiera hacer la actualizacion, puede ser origin-upstream-etc)

NOTA: acostumbrarse a borrar las ramas después de unirlas

podemos incluso viajar a los tags hechos:
git checkout nombretag

para sacar la carpeta git:(ubicado en la carpeta)
 rm -rf .git/




IMPORTANTE: nodemon nombrearchivo para ejecutarlo de manera continua desde git bash