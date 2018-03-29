* Here is the master repo, from the code along for any Questions etc
https://git.generalassemb.ly/jamieking/wdi14-tunr-react-rails

* Getting Started

1) rails new tunr_react_rails --api -d postgresql
cd into dir 

We need to go into the gemfile of the rails dir, and delete some dependencies we don't need anymore:


make sure to init the react app within the rails directory itself and name it 'client'

2 )cd tunr_react_rails
create-react-app client

3) Next we are going to create a package JSON for this root level. For heroku to understand this is a rails and Node app, we need a package JSON file in here to tell eroku what type of node to use. 

create a package.json within the root directory of the rails application and put this inside (make sure the "name"is the name of your project spelled and capped EXACTly correctly or this will all break!) :

{
    "name": "tunr_react_rails",
    "engines": {
      "node": "9.9.0"
    },
    "scripts": {
      "build": "cd client && npm install && npm run build && cd ..",
      "deploy": "cp -a client/build/. public/",
      "postinstall": "npm run build && npm run deploy && echo 'Client built!'"
    }
  }

  The package will run the React app, and copy the minified build folder into the puclic folder in order to produce a fast and efficeient development. 

Under client>package.json, we add this:


  "proxy": "http://localhost:3001",

  underneath the "private" dependencie.

  
