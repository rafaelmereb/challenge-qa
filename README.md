
# Challenge QA Automatization

### Descrição
A equipe de desenvolvimento está criando um jogo, aonde a equipe de QA será responsável por avaliar a qualidade da entrega, então é importante realizar alguns testes e você será responsável por todos eles :)

### O Jogo
Basicamente é um jogo aonde você pode criar um herói para batalhar com os heróis que já existem, todos os personagens tem no mínimo 3 habilidades que são elas: Poder, Velocidade e Combate.
Cada habilidade tem o valor máximo de 200 e o mínimo 0 (zero), para um herói ser válido ele tem que ter todas as habilidades necessárias e não ter um nome comum de outro herói para realizar uma batalha.
 - Obs: Sabemos que há uma falha catastrófica se você encontrar ganha pontos extras.

## Requisitos
 - Você como analista de qualidade deve criar testes automaizados utilizando o Postman
 - Utilizando as APIs abaixo realize os seguintes testes
 - Criando um herói, você deve descobrir um outro herói que você pode vencer.
 - Criando um herói, você deve descobrir um outro herói que você pode perder.
 - Criando um herói, você deve descobrir um outro herói que possui a mesma força.
 - Achar outros cenários de testes também ganham pontos extras.

## O que iremos avaliar
 - Como os testes estão estruturados, nos acreditamos que a organização é muito importante :)
 - Queremos entender a sua abordagem de testes, então é importante você explicar como achou outros cenários de testes.
 - O testes tem uma manutenibilidade fácil, o nome das variáveis fazem sentido?

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
 
 ## Documentação da API
 
**/heroes** [POST]
 
```java
// Input
  {
   "name":"Raiden",
   "skills": {
            "power": 66,
            "velocity": 15,
            "combate": 99
        }
}
// Output
{
    "id": "3b6be017-9633-4832-9b3a-66930a99ca1c",
    "name": "xxxx",
    "skills": {
        "power": 66,
        "velocity": 15,
        "combate": 99
    }
}
 ```
**/heroes/battle** [POST]
 
```java
// Input
  {
    "hero_id":[HERO_ID],
    "machine_hero_id":[HERO_ID]
}
// Output
{
    "winner": "Shazam",
    "loser": "xxxx"
}
 ```
 
Boa sorte!
