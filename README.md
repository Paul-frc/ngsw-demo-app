# ng cli app from scratch with 100 PWA & 100 PageSpeed mobile score

### Overview
```
* fe5ae2e        (HEAD -> master, tag: step-6, origin/master) add cache headers and lorem ipsum content
* 9a0e48d        (tag: step-5) add firebase
* 9be0bef        (tag: step-4) add manifest
* 683be9f        (tag: step-3) add @angular/material style nav
* 9ba7a32        (tag: step-2) ng g component main --module app.module
* 7c60659        (tag: step-1) ng g app-shell shell --universal-app server
* f411c1f        chore: initial commit from @angular/cli
```

## Prerequisites
```
brew install yarn   # recommended, but can use `npm` too
yarn add global @angular/cli http-server
```

## Steps

### 0. Initialize basic app with sw
```
ng new ngsw-demo --service-worker --routing
```

### 1. add app-shell for SSR
```
ng g app-shell shell --universal-app server
yarn
```

### 2. add main module (frontpage)
```
ng g component main --module app.module
```
- add import and route to app-routing module: `{path: '', component: MainComponent}`

### 3. add material elements for navigation
```
yarn add @angular/material @angular/cdk @angular/animations
```
- Import to app.module: `BrowserAnimationsModule`, `MatTabsModule`
- Add styles.css: `@import "~@angular/material/prebuilt-themes/indigo-pink.css";`
- Add `<nav mat-tab-nav-bar> ... </nav>` navigation to app.component template

### 4. add manifest, build SSR
- create src/manifest.json and add it to .angular-cli.json
- add meta to index.html
```
ng build --prod
hs dist
```

### 5. add firebase and deploy
```
firebase init
# only hosting, deploy directory is `dist`
firebase deploy
```
- will score 100 for PWA but poorly on PageSpeed

### 6. add cache headers and content
- add content to `app.component` template
```
ng build --prod
```
- inline `dist/styles...bundle.css` to `dist/index.html`
```
firebase deploy
```
- will score 100 & 100
