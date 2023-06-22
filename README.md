# Hello and welcome to my world!

This site was made using pnpm monorepo! The main portfolio code can be found in packages/portfolio!

All other packages are applications i want to share with the world! This set up allows me to isolate projects while still including them on my site to interact with! The other benefit is that each project has it's own
git repo in it which makes updates easy!!

## To import components between projects
- the host app should export the component or function you'd like to share
- the host app should have a name entry in it's package json with a value like `@portfolio-monorepo/APPLICAITON_NAME` 
- within the remote or client application, run `pnpm add @portfolio-monorepo/APPLICAITON_NAME`
