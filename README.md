# Hello and welcome to my world!

This site was made using pnpm monorepo! The main portfolio code can be found in packages/portfolio!

All other packages are applications i want to share with the world! This set up allows me to isolate projects while still including them on my site to interact with! The other benefit is that each project has it's own
git repo in it which makes updates easy!!

## To import components between projects
- the host app(the project being added) should export the component or function you'd like to share
- the host app should have a name entry in it's package json with a value like `@portfolio-monorepo/APPLICAITON_NAME` 
- within the remote or client application(the app that is going to consume the exported component), run `pnpm add @portfolio-monorepo/APPLICAITON_NAME`

- *IF THE PROJECT BEING ADDED USES A STATE CONTEXT REMEMBER TO ADD IT TO THE CLIENT ROOT PROVIDER OR THE APP WILL NOT FUNCTION CORRECTLY*

## To add submodules
- more info can be found here https://itecnote.com/tecnote/git-issue-with-adding-common-code-as-git-submodule-already-exists-in-the-index/
- git submodule add url_to_repo projectFolderToLink
- e.g. `git submodule add https://github.com/ClydeFrog04/portfolio/ packages/portfolio/`
- if you get `'packages/portfolio' already exists in the index` you need to remove the file from git first with `git rm --cached packages/portfolio/`


## Cloning the project
- in order to clone the project and have it work properly, we also have to clone the submodules. This can be done manually, but a better solution is to run git clone with the `--recursive` flag
- e.g. `git clone --recursive git@github.com:ClydeFrog04/portfolio-monorepo.git`
- this will clone all the projects we need in order to run this project!


## Running this Project
Now that we have our project cloned, we are ready to run the project! 

- ### Install dependencies
  - run `pnpm install` in order to install the project dependencies, this should also install the depencies needed for all of our subprojects *todo* verify if this is true!
- ### Run the project
- - run `pnpm run main` in order to start the project!
- ### Open in browser
- - If your terminal supports it(git bash does not) you can enter `o` in the terminal to open the project in a web browser
- - If your terminal does not support user input when running vite cli, you can manually navigate to the url displayed in the terminal!

## Congrats this project should be able to be opened in a browser now!


## Deploying a pnpm monorepo to services like vercel/netlify
- We have to override the default build and deploy setting since this is *NOT* just a simple react/vite app :]
- Build command is `pnpm run build`
- Output directory is `packages/portfolio/dist` *note that we probably could add a cp to the build command that creates a dist dir at the project root but i wasn't feeling like experimenting at the time of writing :]
- Install command(if applicable, netlify will detect a pnpm-lock.yaml and use pnpm by default, other services may not do this, did not test with vercel) `pnpm install`



### Miscellaneous Notes
- In order for refresh to work in production on different routes, a `_redirects` file must exist in the dist folder with an entry of `/*  /index.html  200`
