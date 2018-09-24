# ngrok

[ngrok](https://ngrok.com/) is incredibly useful for publishing `localhost` servers sa temporary publicly available sites

Install it on your path and then run e.g. 

```bash
ngrok http 8080
```

If you are running a `webpack-dev-server` you'll [need to use](https://stackoverflow.com/questions/45425721/invalid-host-header-when-ngrok-tries-to-connect-to-react-dev-server):
```bash
ngrok http 8080 -host-header="localhost:8080"
```