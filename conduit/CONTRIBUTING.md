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
  - The ENV variables for conduit. You can get these from Henry, or Tony. The structure of the ENV variables are listed in the conduit docs.

## Developing Conduit

- The first thing you need to do is pull from the conduit git. The main branch you will be pulling from the `develop` branch.
- In the conduit repo under `CONTRIBUTING.md`, you should find the proper build steps, along with how to run conduit. Read the whole `Develop` section in this before continuing these docs. 
- Use Postman

### Tips 
- You will generally be working on one module at a time, so when working on a module, it is recommended to open your Code Editor to that specific module directory.
- For every issue that you will work on, create a branch with the naming schema `<Jira ticket #>/<Issue description>` - example `esb-1299/adding product type to product search`.
- Each commit on that branch should follow a similar naming scheme: `<Jira ticket #> <commit description>`
- When you create a PR, use the naming scheme: `<module>: <description>`. E.g. `api-contractor-assist: Updates User Info API to contain Prize information and Adds Prize Endpoint`
