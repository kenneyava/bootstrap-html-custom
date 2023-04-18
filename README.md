# How I Customize Bootstrap 5 Colors

```
# for firefox browser with markdown plugin
file:///C:/users/kaung/vscode/bootstrap-html-custom/README.md
```

Create your project folder

```
npm init
```

Reference: [Bootstrap Starter Kit](https://github.com/twbs/bootstrap-npm-starter) Still BS4, not yet updated for BS5.

So, I just used it to get list of packages to install

installed all the packages listed in package.json
```
npm install bootstrap bootstrap-icons
npm install --save-dev autoprefixer node-sass nodemon npm-run-all postcss postcss-cli purgecss serve stylelint stylelint-config-twbs-bootstrap
```

- Make folder scss
- create file custom.scss inside the folder
- customize variables in this file

used this [article](https://blog.hubspot.com/website/how-to-override-bootstrap-css) to try out.

These are the hundreds of variables you can customize. [variables](https://github.com/twbs/bootstrap-sass/blob/master/assets/stylesheets/bootstrap/_variables.scss)

This [document](https://getbootstrap.com/docs/5.0/customize/overview/) gave some pointers for the process.

create you index.html for testing

Also from package.json above, add the following to your package.json

```json
"scripts": {
    "build": "npm run css",
    "css-compile": "node-sass --include-path node_modules --output-style compressed --source-map true --source-map-contents true --precision 6 scss -o assets/css/",
    "css-lint": "stylelint scss/",
    "css-prefix": "postcss --replace assets/css/starter.css --use autoprefixer --map",
    "css-purge": "purgecss --keyframes --css assets/css/starter.css --content index.html \"node_modules/bootstrap/js/dist/{util,modal}.js\" --output assets/css/",
    "css": "npm-run-all css-compile css-prefix",
    "server": "serve --listen 3000",
    "start": "npm-run-all --parallel watch server",
    "watch": "nodemon -e html,scss -x \"npm run css\"",
    "test": "npm run css-lint && npm run css"
  },
```

```bash
# compiles scss into assets\css
npm run css-compile
# http://localhost:3000
npm run server
```

You can then drop `custom.css` any where you need

----

You do not need to download source code from here [Bootstrap Download](https://getbootstrap.com/docs/5.0/getting-started/download/).

This is only if you are developing to submit mods or enhancements to Bootstrap itself.


