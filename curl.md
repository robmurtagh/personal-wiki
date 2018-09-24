# cURL

## Download raw site HTML

Following commands allows us to see the original HTML etc before Javascript starts running and transforming the DOM:

```bash
curl -D - https://www.google.com/
```

```bash
curl -D - https://www.google.com/ > site.html
```