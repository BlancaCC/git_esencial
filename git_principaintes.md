# Git 

## Qué es git
Git es una herramienta de sistema de control de versiones (SCV). Básicamente, te permite gestionar la historia de cambios de un proyecto, facilitando la cooperación entre desarrolladores. En particular, git es distribuido, lo que significa que cada colaborador tiene una copia íntegra del repositorio original localmente, a diferencia de los SCV centralizados que requieren de una conexión a internet para realizar cambios.  

## Qué es github  

Github, por otra parte, es un servicio remoto para almacenar repositorios git. Existen numerosas alternativas como Gitlab, Bitbucket, Notabug.  

## Instalación y configuración de git   

Abrir terminal y escribir `sudo apt-get install git` en el caso de distribuciones como debian, ubuntu...
En otras distribuciones `sudo pacman -S git`

Tras esto será necesario configurar como mínimo el correo y usuario de la cuenta con que se haya registrado en github, gitlab o cualquier otro servicio. Tenga presente que github ofrece beneficios a estudiantes. 
```
git config --global user.name "NOMBRE"
git config --global user.email CORREO@example.com 
```
| Nota: no olvidar las comillas del nombre, todo esto será modificable a posteriori. 

Con esto ya estaría terminado y configurado git para usarse; sin embargo, también son configurables otros parámetros como el editor de texto, que por defecto suele ser nano. 
Para cambiarlo: `git config --global core.editor "EDITOR"` 

Donde EDITOR es el nombre del editor que dese utilizar, por ejemplo emacs.  

En el caso de utilizar nano, opción que recomiendo personalmente, puede ver sus comandos básicos aquí. (En proceso de creación).

## Uso básico de git

Esencia de lo que se va a hablar:

0. [`git status`](#git-status)
1. [`git pull origin master`](#git-pull)
2. [Por fin puedes realizar tus cambios](#por-fin-puedes-realizar-tus-cambios)
3. [`git add`](#git-add)
4. [`git commit [-am '<titulo>']`](#git-commit)
5. [`git push origin master`](#git-push)

Por su propia naturaleza en necesario trabajar sobre "carpetas", a las que a partir de ahora llamaremos repositorios. Para ello lo más fácil es clonar uno existente o crear uno nuevo desde la propia web.

Para clonar: 

- Copiar enlace del repositorio, por lo general suele existir un botoncico que permite copiar el link.
- Desde la línea de comando posicionarse en el directorio donde se quiera tener la carpeta. 
- Escribir `git clone URL-COPIADA`  

### Comandos para actualizar el repositorio  

- Actualizar el contenido de la misma: `git pull origin master`
`origin master`hace referencia a la rama que se desea actualizar, con el objetivo de no liar mucho al principiante tómelo como meras palabras y cuando esté familiarizado le animo a continuar con su investigación sobre ramas. 
**IMPORTANTE Es una buena construmbre hacer un pull siempre, antes de comenzar a trabajar para evitar conflictos**

- Para actualizar el contenido que usted haya creado: 


### git status

Este comando no es necesario ejecutarlo en un momento particular pero, créeme,
es de gran ayuda. Te aporta información sobre el estado del repositorio. Por ello,
ejecútalo después de cada orden que realices con `git`. Es útil incluso si no entiendes
esa información porque... ¡puedes copiar y pegarla en google!

Sin embargo, los siguientes comandos deberán realizarse ordenadamente, y
constituirán la base para contribuir a un proyecto.

### git pull

```console
$ git pull <remote> <branch-name>
```

- `<remote>`: Es la dirección remota del repositorio, en nuestro caso 
la dirección `origin` apunta a nuestro sitio en los servidores de Github.
- `<branch-name>`: El nombre de la rama. La predeterminada a utilizar suele ser `master`.

Por tanto, la orden que ejecutaremos será `git pull origin master`.

Este comando actualiza tu repositorio local con el remoto. Es decir, "descarga"
el trabajo realizado por los otros. Es importante ejecutarlo siempre antes de empezar a
realizar cambios, para evitar las situaciones en las que dos personas estén modificando
el mismo archivo.

De todos modos, si en algún caso se te olvida, `git` no te permitirá sobreescribir el
repositorio, y te informará de que tienes que hacer `git pull` antes!

### Por fin puedes realizar tus cambios

Esta es la fase donde realizas el trabajo real. Es decir, creas archivos, modificas otros...
En resumen, pasas un rato de diversión.

### git add

```console
$ git add <ruta-archivo>
```

(Así, `git add .` añadiría todo el directorio actual al repositorio.)

Este comando añade a la fase de `staging`, que podríamos llamar como
almacenamiento o pre-commit. Para entendernos, es como una fase de preparación
del commit. Primero preparas todo lo que quieres cambiar (`git add`), y luego
lo fotografías con (`git commit`).

### git commit

```console
$ git commit [-a -m "Título"]
```

Este comando registra los cambios en la historia del repositorio. Es recomendable
ejecutar `git status` antes de hacer ningún commit. Así puedes comprobar que archivos
están añadidos a la fase de preparación del commit (de color verde), antes de registrar
los cambios definitivamente. En realidad, no hay nada definitivo en git, pues es siempre
posible modificar la historia. Pero si trabajas en equipo y has subido cambios erróneos,
no son para nada recomendable comandos arcanos como `git rebase` o `git commit --amend`.

El significado del corchete en la orden es que `-a -m "<Título>"` son
parámetros opcionales.

Por ejemplo:

- `git commit`: Llamará a tu editor por defecto para escribir el mensaje de
commit. Deberás escribir en la primera línea, citando a Blanca "un Título
exclarecedor sin aaaaa". (Recuerda que utilizamos un sistema de gestión de
versiones que es git para controlar mejor los cambios que vamos realizando).
 
- `git commit -a`: Sera un atajo que realizará `git add .` y `git commit` en el
mismo comando. Úsalo sólo si sabes que todo lo que puede añadirse al
repositorio, quieres que sea añadido.
 
 
- `git commit -m "Mensaje del commit"`: Registra el commit con una línea de
mensaje (que se correspondería con la primera línea del archivo que se editaría
con la orden `git commit`.). Recuerda escribir un mensaje de commit adecuado.

Consejos genéricos: 

- Utiliza `git commit -m `: A no ser que quieras escribir descripciones al
  estilo Blanca con `git commit`, no suele ser necesario añadir otra cosa
  más que el título (si este está suficientemente claro).

- Debes intentar que un commit reúna en un mensaje cambios relacionados.
  Ejemplos de títulos pasables son:
   "Corregir erratas" "Actualizar ejercicio tal" "Ejercicio x portado a latex". 

- No valen mensajes como: "mejorando cosas" "ejercicios" "bomba nuclear".
      Los dos primeros por ser ambiguos y el siguiente por absurdo.

4. git push

```console
$ git push <remote> <branch-name>
```

(Normalmente `git push origin master`)

Una vez tienes tus cambios registrados en tu ordenador es hora de compartirlos
con los demás.

Si te fijas la orden es muy parecida a [git pull](#git-pull). Y de hecho 
<remote> y <branch-name> tienen el mismo significado que en esta. Sin embargo,
el objetivo de `git push` es justo el contrario, es decir, subir tus cambios
locales al repositorio remoto.

Recomendación: intenta ejecutar `git push origin master` cada vez que hayas
hecho un commit para evitar conflictos.

### Trabajar con ramas

- `git branch`
- `git checkout <rama>`


Más información en
[git-scm](https://git-scm.com/book/es/v1/Ramificaciones-en-Git-%C2%BFQu%C3%A9-es-una-rama%3F)




