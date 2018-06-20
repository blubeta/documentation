## Follow these steps if we're working from a client's Bitbucket and we want to work internally on Github.

1. git remote remove origin
2. git remote add origin https://{username}@bitbucket.org/{clientOrganization}/{repoName}.git
3. git remote set-url --add --push origin  https://{username}@bitbucket.org/{clientOrganization}/{repoName}.git
4. git remote set-url --add --push origin https://github.com/blubeta/{ourGithubRepo}.git

This allows us to have on "source of truth" (the client' Bitbucket). In other words, we pull only from Bitbucket, and push to our Github remote repo and the client's Bitbucket when we want to push changes up.


