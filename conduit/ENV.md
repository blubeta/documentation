### Environment


- You can get these from Henry, or Tony. The structure of the ENV variables are listed in the conduit docs under `docs/ENVIRONMENT_VARS.md`. They are subject to change so I won't put them here.
- All your env variables are located in `conduit/env`. Honestly I don't think it matters where you put them, but it's best to seperate them out into the files listed in the conduit docs.
- To run a microservice when you run docker-compose up, in the environment variables under NODE_MODULES, you have to list your microservice in that list.
  - Example: You want to work on api-dmi.
  - Before: `NODE_MODULES=branch,inventory,order,customer,product,contractor-assist,customer-inventory`
  - After: `NODE_MODULES=branch,inventory,order,customer,product,contractor-assist,customer-inventory,dmi`
- Any change to the node_modules, I belive you have to recompose docker. (Not 100% on this but I'm 80%).