# upload-vue-to-gh-pages

This project is for you to comfortably upload the `dist` folder of your `vue` project to `github` via the `gh-pages` branch.

It only consist on 1 script, which must be located on `/dev` folder of the project.

### Installation

You can install this project like this from the root of your `vue` project:

`~ git clone {url of this repository} .`

It will add this `README.md` file (be careful to not override a previous one) and a `/dev/upload-to-ghpages.js` file.

### Requirements

You also need to have installed in the `vue`'s `npm` project these tools:

  - `rimraf`
  - `fs-extra`
  - `execute-command-sync`

You can do it all at once like this:

`~ npm i -D rimraf fs-extra execute-command-sync`

Also, you need to have the `package.json#repository.url` fulfilled, as it will be used as reference for the script to know the URL of the repository.

### How to use it

For you to run this script, you only need to:

`~ node dev/upload-to-ghpages.js`

That's all: you will push the current `vue` application to the `gh-pages` branch of your project.

### Execution

These are the steps that follows the script:

1. **BUILD VUE PROJECT**. This step:
  - runs `npm run build` in order to generate the `dist` folder.
2. **CLONE GH-PAGES BRANCH TO A TEMPORARY FOLDER**. This step:
  - creates a temporary folder.
  - clones the `gh-pages` branch of the current repository of the project into this temporary folder.
3. **COPY TEMPORARY FOLDER TO DIST FOLDER AGAIN**. This step:
  - copies the `.git` folder from the temporary folder (which has the `.git` folder of the `gh-pages` branch) to the `dist` folder.
4. **REMOVE TEMPORARY FOLDER**. This step:
  - removes the temporary folder.
5. **PUBLISH DIST FOLDER TO GH-PAGES BRANCH**. This step:
  - runs `git add .` from the `dist` folder (through the `gh-pages` branch)
  - runs `git commit`
  - runs `git push`

This way, you can:
  - upload **fastly and effortlessly** your `vue` applications into the `gh-pages` branch of your project.
  - keep all the branches of the repository for the development
  - keep the `gh-pages` branch only on the `dist` folder.

### License

This project is licensed under (WTFL)[http://www.wtfpl.net/], so do what you want with it.