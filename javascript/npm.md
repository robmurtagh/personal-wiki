# npm

## Create command line utility for project

In your `package.json`, include (see also package.json docs [here](https://docs.npmjs.com/files/package.json)):

```json
{ "bin" : { "myapp" : "./cli.js" } }
```

Making sure the relevant script has the header:

```javascript
#!/usr/bin/env node
```

## Locally install the command line utility

```bash
npm link
```