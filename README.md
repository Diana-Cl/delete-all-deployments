# Delete all Deployments
**Deletes all deployments given a Cloudflare Pages project name**

<br></br> 

#
## How to

### Install dependencies
```js
npm install
```

<br></br> 

### Delete all deployments
> except for the live production deployment  
> > excluding aliased deployments

```js
CF_API_TOKEN=xxx CF_ACCOUNT_ID=xxx CF_PAGES_PROJECT_NAME=xxx npm start
```

<br></br> 

### Delete all deployments
> except for the live production deployment  
> > INCLUDING aliased deployments, eg. my-branch.exampleproj.pages.dev

```js
CF_API_TOKEN=xxx CF_ACCOUNT_ID=xxx CF_PAGES_PROJECT_NAME=xxx CF_DELETE_ALIASED_DEPLOYMENTS=true npm start
```

