# Express Helper

## Express Helper Configure Options

| Property | Required  | Description |
|----------|:---------:|:--------------|
| app      |    :x:    | Express App to be used by http helper if not defined a Express App to be used, Express Helper will create a new instance |
| port     |    :x:    | The port that will be used by the server, if not defined, it will try to use the value defined in the environment variable caled HTTP_PORT, if the environment variable does not exist or is empty the default value will be 80. <br><br> This property acts almost the same in the HTTPS Helper, except it looks for the environment variable named HTTPS_PORT when not set, and defaults to 443 when no other value is found. |
| routes   |    :x:    | Array that contains express.Router or express.Handler, so that it is possible to create application routes and/or create middlewares. |

## Express Helper Configure Options, for HTTPS Servers

All properties mentioned above also apply to HTTPS server configurations.

| Property    | Required           | Description   |
|-------------|:------------------:|:--------------|
| private_key | :heavy_check_mark: | ????              |
| certificate | :heavy_check_mark: | ????              |
| pass_phrase |         :x:        | ????              |

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

## Automatic load express.Routers and express.Handlers

```typescript
import expressHelper, { globRouterLoader } from "express-helper"
const routes = [ globRouterLoader("./routes/**/*.routes.ts") ]
expressHelper.http({ routes })
expressHelper.https({ routes })
```
