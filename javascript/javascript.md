# Javascript

## Spread syntax

Use the [Spread Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) to expand an iterable (e.g. an object) into its components.

An example of merging with shallow clone would be:

```javascript
var obj1 = { a: "b" };
var obj2 = { c: "b" };
var obj3 = { ...obj1, ...obj2 };
console.log(obj3);
```

- `obj3` contains a copy of `obj1` and `obj2` as they were when `obj3` was created
- `obj3` is not a reference to the current state of `obj1` and `obj2`

## Executing asynchronous functions in series and parallel

Example snippet:

```javascript
const executeInSeries = async promises => {
  var results = [];
  for (let promise of promises) {
    results.push(await promise());
  }
  return results;
};

const executeInParallel = promises => {
  return Promise.all(promises);
};

const generateTimeoutPromise = () => {
  return new Promise((resolve, _reject) => {
    setTimeout(() => {
      console.log("COMPLETE: timeoutPromise");
      resolve("RESOLVED: Complete");
    }, 2000);
  });
};

executeInSeries([
  generateTimeoutPromise,
  generateTimeoutPromise,
  generateTimeoutPromise
]).then(results => {
  console.log("COMPLETE: executeInSeries");
  console.log("RESOLVED: executeInSeries");
  console.log(results);
});

executeInParallel([
  generateTimeoutPromise(),
  generateTimeoutPromise(),
  generateTimeoutPromise()
]).then(results => {
  console.log("COMPLETE: executeInParallel");
  console.log("RESOLVED: executeInParallel");
  console.log(results);
});
```

## .prettierrc Configuration

My preferred `.prettierrc` settings are:

```json
{
  "printWidth": 140,
  "trailingComma": "es5",
  "jsxBracketSameLine": true,
  "arrowParens": "always",
  "tabWidth": 4,
  "noSemi": true
}
```

On a JS project I tend to turn on format on save (VSCode > Preferences > Settings > Workspace Settings > `settings.json`)

```json
{
  "editor.formatOnSave": true
}
```

I use a `.prettierignore` for individual files I don't way to format within the project.

Finally I have the following setting to always turn off certain file types from formatting (VSCode > Preferences > Settings > User Settings > `settings.json`):

```json
"[handlebars]": {
  "editor.formatOnSave": false
}
```

## ESLint

ESLint apparently respects the following element of `package.json`:

```json
"engines": {
    "node": ">=10.6.0"
}
```

I tend to also add the following `.eslintrc` to support ES6 features:

```json
{
  "env": {
    "es6": true
  }
}
```
