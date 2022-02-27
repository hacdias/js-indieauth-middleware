# @hacdias/indieauth-middleware

> ⚠️ Package no longer maintained. Please [contact me](https://hacdias.com/contact) if you want to become its maintainer.
> 
This is a simple [IndieAuth](https://www.w3.org/TR/indieauth/) middleware that can be used in conjunction with
Express.js or any other framework that uses a similar API.

## Install

```console
$ npm i --save @hacdias/indieauth-middleware
```

## Usage

This example uses [express.js](https://expressjs.com/) as the middleware framework
but you can use anything as long as you provide an object with the JSON or the form
encoded data.

```javascript
const indieauth = require('@hacdias/indieauth-middleware')
const express = require('express')

const app = express()

app.use(indieauth({
  me: 'https://hacdias.com/',                       // Your domain
  endpoint: 'https://tokens.indieauth.com/token'    // The endpoint used to check the tokens
}))

app.post('/', (req, res) => {
 if (!req.hasScope(['updates'])) {
   // req.hasScope already returns a 401 unauthorized if the user does not
   // have the required scopes.
   return
 }

 // Do your job...
})
```

## Contributing

PRs accepted.

## License

MIT © Henrique Dias
