# Javascript

## Spread syntax

Use the [Spread Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) to expand an iterable e.g. an object into its components.

An example of merging with shallow clone would be:

```javascript
var obj1 = { a: "b" };
var obj2 = { c: "b" };
var obj3 = { ...obj1, ...obj2 };
console.log(obj3);
```

- `obj3` contains a copy of `obj1` and `obj2` as they were when `obj3` was created
- `obj3` is not a reference to the current state of `obj1` and `obj2`

## Executing async functions in series

One way of doing this is:

```javascript
async function executeAsyncFuncsInSeries(promises) {
  for (let promise of promises) {
    await promise();
  }
  return {};
}

const asyncFuncs = argumentList.map(argument => {
  return () => {
    return new Promise((resolve, reject) => {
      functionReturningPromise(argument)
        .then(() => resolve())
        .catch(error =>
          reject({
            error_code: "SOMETHING_CUSTOM",
            error_message: "SOMETHING_INFORMATIVE",
            ...error
          })
        );
    });
  };
});
return executeAsyncFuncsInSeries(asyncFuncs).then(() => {
  console.log("All done...");
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
