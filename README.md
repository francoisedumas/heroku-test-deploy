# heroku-test-deploy

## Steps to deploy a static (using backend API) VueJS frontend app

### Preparing the app

Next steps are taken from 
  - [official source](https://cli.vuejs.org/guide/deployment.html#heroku)
  - [this article](https://betterprogramming.pub/deploying-a-vue-js-app-to-heroku-d16f95c07a04)
```
vue create heroku-test-deploy
cd heroku-test-deploy
```

Create a `static.json` file at the root of the project and add below code
```javascript
{
  "root": "dist",
  "clean_urls": true,
  "routes": {
    "/**": "index.html"
  }
}
```

Commit your changes
```
git add static.json
git commit -m "add static configuration"
```

Create a production build with `npm run build`

### Deploy on Heroku
```
heroku login
heroku create
heroku buildpacks:add heroku/nodejs
heroku buildpacks:add https://github.com/heroku/heroku-buildpack-static
git push heroku main
```

### The app is online!

Visit it [here](https://sleepy-ocean-15206.herokuapp.com)
<img width="856" alt="Screenshot 2564-08-17 at 17 45 14" src="https://user-images.githubusercontent.com/33062224/129758158-6ca7d835-bfb9-4ca9-ac5e-125390de475b.png">

