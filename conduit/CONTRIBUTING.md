### Contributing to conduit

Contributing to conduit is relatively straight-forward, and most of the information and documentation are on the conduit repo, provided by Henry, but I will share some of my experiences and what I found to be best practices.

### Getting Started

## Prerequsites

You need: 
  - Git and access to the conduit bitbucket. 
  - The docker daemon and docker access to the watsco dockerhub. We have an account with access with the username `watsco@blubeta.com`. You can get the current password from Tony.
    - [Install docker](https://docs.docker.com/install/)
  - A VPN connection to watsco. This resets every 90 days, so when you first get it, set a reminder every 90 days to reset it. 
    - At the current time of these docs, Sergio Cruz is the guy you want to talk to to reset it. Slack him when you need the reset.
  - The ENV variables for conduit. Check out the [environment](./ENV.md) page.

## Developing Conduit

- The first thing you need to do is pull from the conduit git. The main branch you will be pulling from the `develop` branch.
- In the conduit repo under `CONTRIBUTING.md`, you should find the proper build steps, along with how to run conduit. Read the whole `Develop` section in this before continuing these docs. 
- Conduit is comprimsed of many micro-services, all that should basically run independent of one another. These are found in the node/src/modules folder. Their naming scheme is `api-*`.

## Postman
- Use Postman to test out the api routes you've created. In this repo is a Postman environment to import.
- Every time you start up conduit, in Postman you have to hit the authenticate route. If you load up the postman environment, it is in the directory authenticate.
- Each directory is a micro-service, and I try to keep it that way.
- The Watsco's Endpoints came from them, but it is a mess. Anytime I don't have a route already in Postman, check there.
