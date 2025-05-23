# Notes
Notes from [Creating a JavaScript action](https://docs.github.com/en/actions/sharing-automations/creating-actions/creating-a-javascript-action)

## Commands run
### Create Project and Packages
```sh
npm init -y
npm install @actions/core
npm install @actions/github
```

### Setup ncc to condense into one file
To install `@vercel/ncc`
```sh
npm i -g @vercel/ncc
```

To compile run the command below. Will generate `dist/index.js` and `dist/licenses.txt` which contains all the licenses of the node_modules you are using.
```sh
ncc build index.js --license licenses.txt
```



## Bullets
- The toolkit `@actions/core` package provides an interface to the workflow commands, input and output variables, exit statuses, and debug messages.
- The toolkit also offers a `@actions/github` package that returns an authenticated Octokit REST client and access to GitHub Actions contexts.
- The `npm install` commands will create the `node_modules` folder.
- Checking in your node_modules directory can cause problems. As an alternative, you can use a tool called `@vercel/ncc` to compile your code and modules into one file used for distribution.
