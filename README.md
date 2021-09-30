
# Challenge QA Automatization

### Descrição

## Layout



## Requisitos

## O que iremos avaliar


## API

```java
  [URL]: https://challenge-fielo-qa.herokuapp.com
  [APP_ID]: MPD4XHcIIGfMA0GCSqGSIbi232QKBgQCh7uxHjWd1CyRgPKiDb3DQEBAQUAA4GNADCB
```

- **/auth** [POST] - Endpoint responsável pela autorização da aplicação, é necessário adicionar a chave `x-app-id` com  `[APP_ID]` 
- **/heroes** [GET] - Endpoint responsável por retornar todos os heróis.
- **/heroes** [POST] - Endpoint responsável por criar um novo herói.
- **/heroes/battle** [POST]- Endpoint responsável fazer a batalha entre heróis.

## Exemplo da autorização
```java
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://challenge-fielo-qa.herokuapp.com/auth',
  'headers': {
    'x-app-id': 'MPD4XHcIIGfMA0GCSqGSIbi232QKBgQCh7uxHjWd1CyRgPKiDb3DQEBAQUAA4GNADCB'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
 ```
 
 ## Resultado da autorização
 
```java
{
    "auth": true,
    "token": "TOKEN_JWT"
}
```

## Exemplo do consumo dos dados
```java
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://challenge-fielo-qa.herokuapp.com/heroes',
  'headers': {
    'x-access-token': 'TOKEN_JWT'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
 ```
Boa sorte!
