# ProjectGenerator
This is Generator Project in AngularJs

# single page application

# first step is to install node js
- download & install nodejs in pc --> https://nodejs.org/en/download/
- command to check node installed version
    - node --version
    - npm --version

# cli.angular.io (install angular command line)
npm install -g @angular/cli

# ng new (New Project Creation)
ng new <project_name>

# angular material
ng add @angular/pwa

# to create new component
ng generate component <FolderName/component_name>

# To start the Angular local server
- ng serve
- ng serve --open

index.html is the entry point in src folder

# To install bootstrap in angular
npm install bootstrap

# To install jquery
npm install jquery

# If you have some old angular project 
- except for doing ng new yourProject --skip-install
- you can copy your node_modules to your new project and run npm install while you are offline.

# To install material-ui
ng add @angular/material

# Some Important Points
- #directive (caputure frontend-> show frontend ) 
- ngForm(utility),
- ngModel(present->directive will work)

# Model class (data store)   
- ng generate model accountInfo



# service class(business logic-> form data collect, encryption)  
- ng g(generate) s(service) accountInfo

- MEAN stack  mongodb, expressjs, angularjs nodejs(javascript runtime) 
- MERN stack  mongodb, expressjs, reactjs nodejs(javascript runtime)

# To create new Node Project (node is javascript runtime)
- ng init --yes   (initializing node js project )

# Execution Flow
- frontend->eventListners(onsubmit, hover)->component.ts->serviceclass->expressServer.


