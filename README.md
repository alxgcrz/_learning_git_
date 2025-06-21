# Git

## Comandos

### Ayuda sobre un comando

```sh
# Abrir el navegador con información sobre un comando 
$ git {command} --help
```

### Configuración

- [8.1 Customizing Git - Git Configuration](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)
- [git-config - Get and set repository or global options](https://git-scm.com/docs/git-config)

#### Mostrar la cofiguración actual

```sh
git config --list
```

#### Mostrar la configuración local

```sh
git config --local --list
```

#### Mostrar la configuración global

```sh
git config --global --list
```

#### Mostrar la configuración del sistema

```sh
git config --system --list
```

#### Establecer un nombre de usuario identificable de forma global

```sh
git config --global user.name "Your name"
```

#### Establecer una dirección de correo identificable de forma global

```sh
git config --global user.email "your_mail@mail.com"
```

#### Establecer coloreado automático de la línea de comandos de Git para una fácil revisión

```sh
git config --global color.ui auto
```

#### Establecer el editor global para commits

```sh
git config --global core.editor vi
git config --global core.editor "code --wait"
```

#### Establecer la rama por defecto

```sh
git config --global init.defaultBranch main
```

### Archivos de Configuración

#### Archivo de configuración específico del repositorio [--local]

```sh
<repo>/.git/config
```

#### Archivo de configuración específico del usuario [--global]

```sh
~/.gitconfig
```

#### Archivo de configuración del sistema [--system]

```sh
/etc/gitconfig
```

### Crear

#### Clonar un repositorio existente

Existen dos maneras:

Vía SSH:

```sh
git clone ssh://usuario@dominio.com/repo.git
```

Vía HTTP:

```sh
git clone http://dominio.com/usuario/repo.git
```

#### Crea un nuevo repositorio local

```sh
git init
```

#### Realizar un _clone_ de forma local desde la carpeta del proyecto a otra carpeta

```sh
git clone . /folder/to/the/project
```

### Cambios Locales

#### Cambios en el directorio de trabajo

```sh
git status
```

#### Cambios en archivos rastreados

```sh
git diff
```

#### Agregar todos los cambios actuales al siguiente commit

```sh
git add .
```

#### Agregar algunos cambios de &lt;archivo&gt; para el siguiente commit

```sh
git add -p <archivo>
```

#### Realizar un commit de todos los cambios locales en los archivos rastreados

```sh
git commit -a
```

#### Realizar un commit de los cambios previamente almacenados en el área de pruebas (stage area)

```sh
git commit
```

#### Realizar un commit con un mensaje

```sh
git commit -m 'Aquí el mensaje'
```

#### Realizar un commit saltándose el área de pruebas y agregando un mensaje

```sh
git commit -am 'aquí el mensaje'
```

#### Realizar un commit a alguna fecha anterior

```sh
git commit --date="`date --date='n day ago'`" -am "Mensaje del commit"
```

#### Cambiar último commit

> :warning: **¡No modificar commits ya publicados!** :warning:

```sh
git commit -a --amend
```

#### Cambiar fecha del último commit

```sh
GIT_COMMITTER_DATE="date" git commit --amend
```

#### Cambiar fecha del autor del último commit

```sh
git commit --amend --date="date"
```

#### Mover cambios no confirmados (uncommitted changes) de la rama actual a otra rama

```sh
git stash
git checkout branch2
git stash pop
```

#### Restaurar cambios del área de pruebas (stage area) a la rama actual

```sh
git stash apply
```

#### Eliminar la última serie de cambios del área de pruebas (stage area)

```sh
git stash drop
```

### Historial de Commits

- [Git Basics - Viewing the Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [git-log - Show commit logs](https://git-scm.com/docs/git-log)

#### Mostrar todos los commits, empezando por los más recientes (se mostrará el hash, información sobre el autor, fecha y título del commit)

```sh
git log
```

#### Mostrar todos los commits (sólo se mostrará el hash y el mensaje del commit)

```sh
git log --oneline
```

#### Mostrar todos los commits de un usuario específico

```sh
git log --author="usuario"
```

#### Mostrar los cambios a través del tiempo de un archivo específico

```sh
git log -p <archivo>
```

#### Mostrar commmits que están presentes sólamente en remote/branch al lado derecho

```sh
git log --oneline <origin/master>..<remote/master> --left-right
```

#### Mostrar reference log

```sh
git reflog show
```

#### Borrar reference log

```sh
git reflog delete
```

#### Mostrar el SHA1 del último commit de cada ref

```sh
git ls-remote <repo>
```

### Ramas & Etiquetas

#### Listar todas las ramas locales

```sh
git branch
```

#### Listar todas las ramas remotas

```sh
git branch -r
```

#### Listar todas las ramas locales y remotas

```sh
git branch -a
```

#### Listar sólo las ramas remotas y el commit

```sh
git branch -rv
```

#### Cambiar rama HEAD

```sh
git checkout <rama>
```

#### Crear nueva rama y cambiar a esta

```sh
git checkout -b <rama>
```

#### Crear nueva rama basada en la rama HEAD actual

```sh
git branch <nueva-rama>
```

#### Crear nueva rama de seguimiento basada en una rama remota

```sh
git branch --track <nueva-rama> <repositorio>/<rama-remota>
```

#### Eliminar una rama local

```sh
git branch -d <rama>
```

#### Forzar eliminación de una rama local

> :warning: **¡Se perderán los cambios sin fusionar!** :warning:

```sh
git branch -D <branch>
```

#### Borrar rama remota

```sh
git push [remote] :[branch]
```

#### Marcar el commit actual con una etiqueta

```sh
git tag <tag-name>
```

#### Marcar el commit actual con una etiqueta que incluye un mensaje

```sh
git tag -a <etiqueta>
```

#### Borrar la etiqueta local '12345'

```sh
git tag -d 12345
```

#### Borrar la etiqueta remota '12345' (eg, GitHub version too)

```sh
git push origin :refs/tags/12345
```

Otra forma:

```sh
git push --delete origin tagName
```

### Actualizar & Publicar

#### Listar todos los repositorios remotos configurados actuales

```sh
git remote -v
```

#### Mostrar información sobre un remoto

```sh
git remote show <remoto>
```

#### Agregar un nuevo repositorio, nombrado 'remoto'

```sh
git remote add <remoto> <url>
```

#### Descargar todos los cambios de &lt;remoto&gt;, pero no integrarlos al HEAD

```sh
git fetch <remoto>
```

#### Descargar cambios y fusionarlos/integrarlos directamente al HEAD

```sh
git remote pull <remote> <url>
```

#### Obtener todos los cambios del HEAD al repositorio local

```sh
git pull origin master
```

#### Obtener todos los cambios del HEAD al repositorio local sin fusionar

```sh
git pull --rebase <remote> <branch>
```

#### Publicar cambios locales en un remoto

```sh
git push remote <remoto> <rama>
```

#### Eliminar una rama en el remoto

```sh
git push <remoto> :<rama> (desde Git v1.5.0)  
git push <remoto> --delete <rama> (desde Git v1.7.0)
```

#### Publicar tus etiquetas

```sh
git push --tags
```

### Fusionar y _Rebase_

#### Fusionar "rama" en tu HEAD actual

```sh
git merge <rama>
```

#### Hacer un _rebase_ de tu actual HEAD sobre "rama"

> :warning: **¡No hacer _rebase_ de commits ya publicados!** :warning:

```sh
git rebase <rama>
```

#### Aborta un _rebase_

```sh
git rebase --abort
```

#### Continuar un _rebase_ después de resolver conflictos

```sh
git rebase --continue
```

#### Usar tu herramienta de fusión configurada para resolver conflictos

```sh
git mergetool
```

#### Usar tu editor para manualmente resolver conflictos y (después de resueltos) marcar el archivo como resuelto

```sh
git add <archivo-resuelto>
```

```sh
git rm <archivo-resuelto>
```

#### Aplastando commits (squashing)

```sh
git rebase -i <commit-just-before-first>
```

Ahora reemplazando esto,

```sh
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

con esto,

```sh
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

### Deshacer

#### Descartar todos los cambios locales en tu directorio de trabajo

```sh
git reset --hard HEAD
```

#### Sacar todos los archivos del área de pruebas (es decir, deshacer el último `git add`)

```sh
git reset HEAD
```

#### Descartar cambios locales de un archivo específico

```sh
git checkout HEAD <archivo>
```

### Desechar todos los cambios de los archivos

```sh
git checkout .
```

#### Revertir un commit (produciendo un nuevo commit con los cambios contrarios)

```sh
git revert <commit>
```

#### Reestablecer tu puntero HEAD a un commit anterior y descartar todos los cambios desde entonces

```sh
git reset --hard <commit>
```

#### Volver al índice de un commit (HEAD@{index})

```sh
git reset HEAD@{index}
```

#### Reestablecer tu puntero HEAD al estado actual de una rama remota

```sh
git reset --hard <remote/branch> es decir, upstream/master, origin/my-feature
```

#### Reestablecer tu puntero HEAD a un commit anterior y preservar todos los cambios en el área de pruebas (stage area)

```sh
git reset <commit>
```

#### Reestablecer tu puntero HEAD a un commit anterior y preservar los cambios locales sin confirmar (uncommitted changes)

```sh
git reset --keep <commit>
```

#### Remover los archivos que fueron accidentalmente agregados al commit antes de ser añadidos al fichero '.gitignore'

```sh
git rm -r --cached .
git add .
git commit -m "remove xyz file"
```

### Debugging

- [Debugging with Git](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)
- [Appendix C: Git Commands - Debugging](https://git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Debugging)
- [git-bisect - Use binary search to find the commit that introduced a bug](https://git-scm.com/docs/git-bisect)
- [git-blame - Show what revision and author last modified each line of a file](https://git-scm.com/docs/git-blame)
- [git-grep - Print lines matching a pattern](https://git-scm.com/docs/git-grep)

#### Quién cambió, qué y cuándo en 'archivo'

```sh
git blame <archivo>
```

#### Buscar un texto en todos los archivos del directorio de trabajo actual

```sh
git grep "cadena_a_buscar"
```

#### Buscar un texto en la versión especificada

```sh
git grep "cadena_a_buscar" v2.5
```

## Extra

### Resumen de comandos para nuevo repositorio

```sh
git init
git add --all
git commit -m "First Commit"
git tag -a v1.0.0 -m "Message"
git remote add origin {url}
git push -u origin master
git clone {url}
git push [remote] --all
git push [remote] --tags
```

### Actualizar un 'fork' de un proyecto remoto

Mantener el 'fork' de un proyecto actualizado con los cambios del autor original:

```sh
# Clonar nuestro fork del otro proyecto
$ git clone git@github.com:YOUR-USERNAME/YOUR-FORKED-REPO.git

# Añadir la URL del repositorio original
$ cd into/cloned/fork-repo
$ remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
$ git fetch upstream

# Actualizar su bifurcación desde el repositorio original para mantenerse al día con sus cambios
$ git pull upstream master
```

### Cambiar commits

Cambiar la dirección de correo de todos los commits de un repositorio:

```bash
git filter-branch -f --env-filter '
    if test "$GIT_AUTHOR_EMAIL" != "your_email@mail.com"
    then
        GIT_AUTHOR_EMAIL=your_email@mail.com
    fi
    if test "$GIT_COMMITTER_EMAIL" != "your_email@mail.com"
    then
        GIT_COMMITTER_EMAIL=your_email@mail.com
    fi
' -- --all
```

### Git Large File Storage (LFS)

```sh
git lfs install` # You only need to run this once per user account
git lfs track "*.psd"`
git add .gitattributes` # Now make sure _.gitattributes_ is tracked
git add file.psd`
git commit -m "Add design file"`
git push origin master`
```

- [Más información](https://git-lfs.github.com/)

## Github CLI

- [Sitio oficial](https://cli.github.com/manual/)

### Configuración

```sh
# Autenticarse con la cuenta de Github
$ gh auth login

# Mostrar información de la autenticación
$ gh auth status
```

### Mostrar la lista de repositorios

```sh
gh repo list
```

---

## Enlaces

### Git

- 🔸 [Git](https://git-scm.com/)
- [JitPack - Publish your JVM and Android libraries](https://jitpack.io/)
- [Take GitHub to the command line](https://cli.github.com/)
- [GitHub Actions](https://github.com/features/actions)
- [Creating a Killer GitHub Profile README](https://dev.to/dailydotdev/creating-a-killer-github-profile-readme-part-1-33nm)
- [Beautify your GitHub Profile](https://dev.to/philiphaines/beautify-your-github-40hh)
- [Keeping Git Commit Messages Consistent with a Custom Template](https://dev.to/timmybytes/keeping-git-commit-messages-consistent-with-a-custom-template-1jkm)

### Git - Learning

- <https://github.com/git-tips/tips>
- 📑 <https://github.com/arslanbilal/git-cheat-sheet>
- <https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf>
- <http://ndpsoftware.com/git-cheatsheet.html>
- <http://ohshitgit.com>
- <https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-es.md>
- <https://github.com/git-tips/tips>
- <https://codewords.recurse.com/issues/two/git-from-the-inside-out>
- <https://cli.github.com/>
- <https://udacity.github.io/git-styleguide/>
- 🎓 [Documentación de GitHub](https://docs.github.com/es)
- 🎓 [Training GitHub](https://training.github.com/)
- 🎓 [Get started with GitHub documentation](https://docs.github.com/en/get-started)
- 🎓 [Git Tutorials and Training | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials)
- 🎓 [Git and GitHub: The Complete Guides](https://dev.to/ifierygod/git-and-github-the-complete-guides-chapter-1-23cp)
- 📑 [First Aid git](http://firstaidgit.io/#/)
- 📑🇪🇸 [Tips: Más de 100 comandos para GitHub / Git que deberías conocer | Desde Linux](http://blog.desdelinux.net/tips-mas-de-40berias-conocer/)
- 📑🇪🇸 [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/index.es_ES.html)
- 📑🇪🇸 [Git: Mini Tutorial y chuleta de comandos](http://elbauldelprogramador.com/mini-tutorial-y-chuleta-de-comandos-git/)
- ⭐🇪🇸 [Una guía para programadores usando git acerca de qué hacer cuando las cosas van mal](https://github.com/k88hudson/git-flight-rules/blob/master/README_es.md)
- 🎓 [A Hacker’s Guide to Git | Wildly Inaccurate](http://wildlyinaccurate.com/a-hackers-guide-to-git/)

### Git - Books

- 📕🇪🇸 [Git - Book](https://git-scm.com/book/es/v2)
- 📕🇪🇸 [Pro Git, el libro oficial de Git](https://uniwebsidad.com/libros/pro-git)
- 📕 <https://goalkicker.com/GitBook/>

## Licencia

[![Licencia de Creative Commons](https://i.creativecommons.org/l/by-sa/4.0/80x15.png)](http://creativecommons.org/licenses/by-sa/4.0/)
Esta obra está bajo una [licencia de Creative Commons Reconocimiento-Compartir Igual 4.0 Internacional](http://creativecommons.org/licenses/by-sa/4.0/).
