# Developing

Conduit is comprimsed of many micro-services, all that should basically run independent of one another. These are found in the node/src/modules folder. Their naming scheme is `api-*`.

I'd recommend also reading the whole CONTRIBUTING page in conduit's root directory. 

## Postman
- Use Postman to test out the api routes you've created. In this repo is a Postman environment to import.
- Every time you start up conduit, in Postman you have to hit the authenticate route. If you load up the postman environment, it is in the directory authenticate.
- Each directory is a micro-service, and I try to keep it that way.
- The Watsco's Endpoints came from them, but it is a mess. Anytime I don't have a route already in Postman, check there.


## Modifying APIs
- Generally, most of your work will consist of modifying one of the microservices.
- The API endpoints generally follow this flow: `Route` > `Controller` > `Service` 
- Sometimes the Service interacts with Data directly, sometimes there's a data layer already.
  - Example: Sometimes Services will call a SQL query, while sometimes Services will import a funciton that calls the SQL query.
- I generally try to use Sequelize when I can. But some of the endpoints use knex (or even xml). My rule of thumb is to basically follow the patterning of the microservice, which you just have to look at. 

## Updating Schema
- Whenever you modify an API's request parameters or response body, you have to update the schema.
- Schema's are found under `schemas/` in the root level of the microservice.
- Example Schema:
``` 
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "type": "object",
    "additionalProperties": false,
    "properties": {
        "list_id": {
            "$ref": "http://api.dev.ductoid.com/schema/customer-inventory#/definitions/field/list_id"
        },
        "approved": {
            "$ref": "http://api.dev.ductoid.com/schema/dmi#/definitions/field/approved"
        },
        "source": {
            "$ref": "http://api.dev.ductoid.com/schema/dmi#/definitions/field/source",
            "default": "DMI"
        },
        "suppliers": {
            "$ref": "http://api.dev.ductoid.com/schema/dmi#/definitions/field/suppliers"
        }
    },
    "required": [
        "list_id"
    ]
}
``` 

- This is the request schema for `CreateROR`. Pretty simple to understand I think.
- I'm not sure what the `"$schema"` field is for, I never really use it, so ignore that.
- `type` - `"object"`, `"string"`, etc...
  - Sometimes Henry uses custom types, but very rarely do you need to.
- `"$ref"` - References another definition somewhere else. In this case we are referring to a definition in our dmi microservices `schema/definitions.json`. 
  - Generally you want to create most of your definitions in that main `definitions.json` file and then reference them.
  - An example of a definition is:
    ```
        "example": {
          "type": "string",
          "description": "This is an example for blubeta"
        }
    ```
- `"required"`: The schema validates that these exist in the request, and if not, there will be a validation error.
- The schema structure is the same for both request and response, the type and the definitions are different though.
- IMPORTANT: Whenever you update a schema, before you submit the PR, run `node apidoc.js` in the `node/src` directory. This will actually update the docs.  
  - I always make sure to commit everything before I do this, and then run it as a seperate commit. Because things can go wrong and I just throw away the changes if they do, fix the changs, and re-run the script.




## Testing

- On every micro-service, before you submit a PR, make sure to run `npm test`. If any tests fails, fix them. 
- I'm not an expert on tests, but you can generally figure out how to update the tests with context clues.

## Auth Code on GM
- In the app if you go to Product Search (search bar at top of home screen), enter ?951159? and tap search, now if you tap on the menu icon you should see  ‘Debug’ at the bottom, tap that and you’ll see a link to ‘Copy Token’, that will copy to your clipboard and you just need to send it to your laptop.