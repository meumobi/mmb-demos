mmb-demos is a [firebase project hosting multi-sites](https://firebase.google.com/docs/hosting/multisites) of demos shared as open source project from meumobi.

## Create new demo

1. Firebase Hosting: Add additional site
    -  Should be done directly from [Firebase Hosting page](https://console.firebase.google.com/u/0/project/meu-starter/hosting/main) of mmb-demos project. Use [PROJECT-NAME] as subdomain.
2. Create new github repo
    - named mmb-demos.[PROJECT-NAME]
3. Import submodule
    - Import new project as submodule on mmb-demos `$ git submodule add https://github.com/meumobi/mmb-demos.[PROJECT-NAME].git`

4. Define the hosting configuration

Add on `firebase.json``

```json
  {
    "target": "[PROJECT-NAME]",
    "public": "mmb-demos.[PROJECT-NAME]/www",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
```
5. Set up deploy target
   - `$ firebase target:apply hosting [PROJECT-NAME] [PROJECT-NAME]`
6. Serve locally
    - `firebase serve --only hosting:[PROJECT-NAME]`

## Deploy demo

1. Build project
2. Deploy
    - `$ firebase deploy --only hosting:[PROJECT-NAME]`
  