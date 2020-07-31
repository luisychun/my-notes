---
title: "Deploy Vue App in Github Pages"
date: 2020-06-17T20:38:01+08:00
tags: ["Vue", "Github Pages"]
draft: false
---

### Reference
[Deploy to Github Pages like a pro with Github Actions](https://dev.to/rolanddoda/deploy-to-github-pages-like-a-pro-with-github-actions-4hdg)

### Deploy Vue App in GitHub Pages

Create **vue.config.js** in your project root directory and add **publicPath: ‘/your-repos-name**

Create a scripts folder and add **deploy.js**, add following scripts

{{< rawhtml >}}
  <p class="show-in-mobile">
    <a href="https://gist.github.com/luisychun/b20b834b9ba4189b8be646f9b992ee40" target=_blank>Gist</a>
  </p>
{{< /rawhtml >}}

{{< rawhtml >}}<div class="hide-in-mobile">{{< /rawhtml >}}
```javascript
  const execa = require(“execa”);
  const fs = require(“fs”);

  (async () => {
    try {
      await execa(“git”, [“checkout”, “—orphan”, “gh-pages”]);
      console.log(“Building…”);
      await execa(“npm”, [“run”, “build”]);
      // Understand if it’s dist or build folder
      const folderName = “dist”;
      await execa(“git”, [“—work-tree”, folderName, “add”, “—all”]);
      await execa(“git”, [“—work-tree”, folderName, “commit”, “-m”, “gh-pages”]);
      console.log(“Pushing to gh-pages…”);
      await execa(“git”, [“push”, “origin”, “HEAD:gh-pages”, “—force”]);
      await execa("rm", ["-r", folderName]);
      await execa(“git”, [“checkout”, “-f”, “master”]);
      await execa(“git”, [“branch”, “-D”, “gh-pages”]);
      console.log(“Successfully deployed”);
    } catch (e) {
      console.log(e.message);
      process.exit(1);
    }
  })();
```
{{< rawhtml >}}</div>{{< /rawhtml >}}

Open **package.json** and add **“execa”: “latest”** in **devDependecies**

Append **“gh-pages-deploy”: “node scripts/deploy.js”** in **scripts** section, run **npm install** to install added dependencies

Run **npm run gh-pages-deploy** to start the deployment

If run into your node_modules files is broken, run **rm -rf node_modules** and **npm cache clean —force**, it will delete entire node_modules files in your project

Run **npm install** to reinstall required dependencies of your project