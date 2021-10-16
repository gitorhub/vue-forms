# vue-forms
```
title: Vue forms github pages
```

[https://gitorhub.github.io/vue-forms/](https://gitorhub.github.io/vue-forms/)

## TO DEPLOY VUE PROJECT INTO GITHUB PAGES

### create a vue.config.js file

```javascript
module.exports = {
    publicPath: "/vue-forms/"
  }

```

### create a deploy.sh file

```sh
#!/usr/bin/env sh

# abort on errors
set -e

# build
npm run build

# navigate into the build output directory
cd dist

# if you are deploying to a custom domain
# echo 'www.example.com' > CNAME

git init
git add -A
git commit -m 'deploy'

# if you are deploying to https://<USERNAME>.github.io
# git push -f git@github.com:<USERNAME>/<USERNAME>.github.io.git main

# if you are deploying to https://<USERNAME>.github.io/<REPO>
 git push -f https://github.com/gitorhub/vue-forms.git main:gh-pages

cd -

```

### in package.json add script

```json
    "deploy": "sh deploy.sh"
```

### then run command 

```cmd
npm run deploy

```