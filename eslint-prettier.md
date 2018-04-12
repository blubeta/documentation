# ESLint & Prettier Config for VS Code

## Initial setup

1.  Install ESLint extension by Dirk Baeumer.
2.  Install Prettier - Code formatter by Esben Petersen.
3.  Install ESLint globally [npm i -g eslint](https://www.npmjs.com/package/eslint).

## Usage

### ESLint

Now that you've installed ESLint globally, you can run `eslint --init` within your project directory to generate a `.eslintrc` file which will determine how ESLint handles the linting of your JS files.

When you generate an `.eslintrc` file via the eslint cli, you will have the ability to build a config file based on popular style guides, like Airbnb and Google. Airbnb FTW! :)

The main benefit of ESLint is that every single rule is a plugin and you can add more at runtime. That means we can add plugins, like eslint-plugin-react, to provide ESLint with more context to lint our files more accurately. We can talk more about the rules and plugins we decide on as a team, and setup a global ESLint config file to keep our configs uniform.

[Here's](https://eslint.org/docs/user-guide/configuring) the link to the configuration documentation from ESLint docs.

### Prettier

[Prettier](https://prettier.io/) is an opinionated code formatter that watches your files and formats your code based on config settings. It's pretty flexible and integrates seamlessly with VSCode through the Prettier - Code extension. For example, once the extension is installed, Prettier will respect your `editor.formatOnSave` workspace settings. So, your files can format on save. You can even set up [pre-commit hooks](https://prettier.io/docs/en/precommit.html) to have Prettier re-format your staged files. :fire: :fire: :fire:

### TL;DR

1.  ESLint does static analysis on our JavaScript and JSX and ensures it adheres to specific guidelines.
2.  Prettier allows us to set strict guidlines for how we want our code to be formatted, and will format our code on specified actions.
3.  [Read this](https://prettier.io/docs/en/comparison.html) to learn why using these tools in tandem is :fire:
