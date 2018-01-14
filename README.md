# Token Manager

A polymer element that allow manage a token, this can handle a storing and refreshing the access-token

## Installation

```
bower install --save framled/token-manager
```

## Usage
### <token-manager>

Element to manage a access token
```
<link rel="import" href="components/token-manager/token-manager.html">
<token-manager path='token' auto></token-manager>
```

you have to define your custom refresh function, example:

```
function refreshing() {
if(!ajax) {
  ajax = document.createElement('iron-ajax');
}

ajax.url = 'demo.json';
ajax.body = {'token': 'secret'}
ajax.debounce = 5000;
const request = ajax.generateRequest();

return request.completes
  .then(req => (
    Promise.resolve(req.response.token)
  ))
  .catch((error) => {
    console.log(error);
  });
}
const manager = document.createElement('token-manager');
manager.setRefresh(refreshing);
```

### <token-manager-ajax>

Wrapper element that allow you authenticate using the access-token, stored at local or session storage

```
<token-manager-ajax auth-required></token-manager-ajax>
```

## Contributing
1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D
