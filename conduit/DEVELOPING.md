# Developing

Conduit is comprimsed of many micro-services, all that should basically run independent of one another. These are found in the node/src/modules folder. Their naming scheme is `api-*`.

I'd recommend also reading the whole CONTRIBUTING page in conduit's root directory. 

## Modifying APIs
- Generally, most of your work will consist of modifying one of the microservices.

## Postman
- Use Postman to test out the api routes you've created. In this repo is a Postman environment to import.
- Every time you start up conduit, in Postman you have to hit the authenticate route. If you load up the postman environment, it is in the directory authenticate.
- Each directory is a micro-service, and I try to keep it that way.
- The Watsco's Endpoints came from them, but it is a mess. Anytime I don't have a route already in Postman, check there.

