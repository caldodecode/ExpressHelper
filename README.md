# Express Helper

## Express Helper Configure Options

```typescript
interface TExpressHelperConfig {
  // Express App to be used by http helper
  // if not defined a Express App to be used, it will create a new instance
  app?: express.Application
  
  // The port that will be used by the server, 
  // if not defined, it will try to use the value defined in the environment variable caled HTTP_PORT, 
  // if the environment variable does not exist or is empty the default value will be 80.
  // This property acts almost the same in the HTTPS Helper, except it looks for the environment variable named 
  // HTTPS_PORT when not set, and defaults to 443 when no other value is found.
  port?: number
  
  // Array that contains express.Router or express.Handler, so that it is possible to create application routes 
  // and/or create middlewares.
  routes?: (express.Router | express.Handler)[]
}
```

```typescript
interface THttpsExpressHelperConfig extends TExpressHelperConfig {
  private_key: string
  certificate: string
  pass_phrase: string
}
```

## Create a HTTP/HTTPS Server

```typescript
import expressHelper from "express-helper"
expressHelper.http()
expressHelper.https()
```

## Create a HTTP/HTTPS Server Sharing same express.Application

```typescript
import expressHelper from "express-helper"
import express from "express"

const app = express()

expressHelper.http({ app })
expressHelper.https({ app })
```
