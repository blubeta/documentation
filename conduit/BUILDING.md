# Contributing to conduit

Contributing to conduit is relatively straight-forward, and most of the information and documentation are on the conduit repo, provided by Henry, but I will share some of my experiences and what I found to be best practices.

## Getting Started

### Prerequsites

You need: 
  - Git and access to the conduit bitbucket. 
  - The docker daemon and docker access to the watsco dockerhub. We have an account with access with the username `watsco@blubeta.com`. You can get the current password from Tony.
    - [Install docker](https://docs.docker.com/install/)
  - A VPN connection to watsco. This resets every 90 days, so when you first get it, set a reminder every 90 days to reset it. 
    - At the current time of these docs, Sergio Cruz is the guy you want to talk to to reset it. Slack him when you need the reset.
  - The ENV variables for conduit. Check out Environment below.


### Environment

- You can get these from Henry, or Tony. The structure of the ENV variables are listed in the conduit docs under `docs/ENVIRONMENT_VARS.md`. They are subject to change so I won't put them here.
- All your env variables are located in `conduit/env`. Honestly I don't think it matters where you put them, but it's best to seperate them out into the files listed in the conduit docs.
- To run a microservice when you run docker-compose up, in the environment variables under NODE_MODULES, you have to list your microservice in that list.
  - Example: You want to work on api-dmi.
  - Before: `NODE_MODULES=branch,inventory,order,customer,product,contractor-assist,customer-inventory`
  - After: `NODE_MODULES=branch,inventory,order,customer,product,contractor-assist,customer-inventory,dmi`
- Any change to the node_modules, I belive you have to recompose docker. (Not 100% on this but I'm 80%).

## Building Conduit

- The first thing you need to do is pull from the conduit git. The main branch you will be pulling from is the `develop` branch.
- In the conduit repo under `CONTRIBUTING.md`, you should find the proper build steps under `Develop`, along with how to run conduit.

