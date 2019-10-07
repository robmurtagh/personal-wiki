# cURL

## Download raw HTML

The following allows us to see the original HTML etc before Javascript starts running and transforming the DOM:

```bash
curl -D - https://www.google.com/
```

```bash
curl -D - https://www.google.com/ > site.html
```
