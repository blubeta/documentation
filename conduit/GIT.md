# Git Flow

Conduit uses the git rebase flow for their downstream branches, and uses Pull Requests to merge into an upstream branch.

### Branches and Commits

- For every issue that you will work on, create a branch with the naming schema `<Jira ticket #>/<Issue description>` - example `esb-1299/adding product type to product search`.
- Each commit on that branch should follow a similar naming scheme: `<Jira ticket #> <commit description>`

### Pull Requests
- IMPORTANT: Before every PR, make sure to 
  - Run `npm test`. All tests must pass, if they don't fix them.
  - IF you update the schema, run `node apidoc.js` in `conduit/node/src` to update the docs, make sure it works.
- Create Pull Requests on Bitbucket, always into develop.
- Use the naming scheme: `<module>: <description>`. E.g. `api-contractor-assist: Updates User Info API to contain Prize information and Adds Prize Endpoint`
- I usually leave the Description as whatever the commits were, never a problem.
- At my time (February 2018-March 209), my reviewer was Henry Williams every time. So that should be htat.

