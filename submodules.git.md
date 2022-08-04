# Git submodules

https://git-scm.com/book/en/v2/Git-Tools-Submodules

A partir de los repositorios iniciales de la edición 2022_05
es posible ir añadiéndolos como sub-módulos en los repos base

https://github.com/alce65Coders-22-05/01_git
https://github.com/alce65Coders-22-05/02-sass
https://github.com/alce65/03-js
https://github.com/alce65/04-ts
https://github.com/alce65/05-web
https://github.com/alce65/06-web-ts
https://github.com/alce65/07-todo-ts
https://github.com/alce65/08-react
https://github.com/alce65/09-todo
https://github.com/alce65/10-flux
https://github.com/alce65/11-redux
https://github.com/alce65/12-GoT
https://github.com/alce65/13-todo-ng
https://github.com/alce65/15-sever
https://github.com/alce65/16-express
https://github.com/alce65/17-full-express
https://github.com/alce65/18-final-express

```shell
cd week1/workspaces
git submodule add https://github.com/alce65/01_git 00_git
```

Se crea el sub-módulo 00-git como un workspace del proyecto week1

El fichero .gitmodules recoge el correspondiente valor

```.gitmodules
[submodule "workspaces/00-git"]
	path = workspaces/00-git
	url = https://github.com/alce65/01_git
```

Antes de continuar se reorganizan los repos github en una organización:

-   alce65Coders-22-05

```shell
cd week1/workspaces
git submodule add https://github.com/alce65Coders-22-05/02-sass 03_sass
```

Se modifica el nombre en package.json, para que se ajuste al formato de los workspaces

```json (package.json)
{
    "name": "@week01/03-sass"
}
```

Para actualizar la instalación en node_module global,
se ejecuta `npm i` a nivel del proyecto (week01)

Se comprueba el funcionamiento del compilador de SASS

```shell
cd /workspaces/sass
npm run sass
```
