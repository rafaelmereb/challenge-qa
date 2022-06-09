
# QA Automation Challenge

### Description
The development team is creating a game, where the QA team is responsible for the quality of the delivery, so it is important to do some testing and you will be responsible for creating and running the automated test scenarios.

### The Game
Basically it's a game where you can create a hero to battle with the heroes that already exist, all characters have at least 3 skills which are: Power, Speed and Combat.
Each skill has a maximum value of 200 and a minimum value of 0 (zero), for a hero to be valid it must have all the necessary skills and not have a common name of another hero to carry out a battle.
 - Note: We know that there is a catastrophic failure if you find it earns extra points.

## Requirements
 - You as an automation engineer must create automated tests using Postman.
 - Using the APIs below, perform the following tests.
 - The User must be properly authenticated to use the system.
 - By creating a hero, you must discover another hero that you can beat.
 - By creating a hero, you must discover another hero that you might lose.
 - Creating a hero, you must discover another hero who possesses the same strength.
 - Finding other test scenarios also earns extra points.

## what are we going to evaluate
 - Testing strategy.
 - Coverage of Game features.
 - As the tests are structured, we believe that organization is very important :)
 - We want to understand your testing approach. So it's important that you explain through comments how you found and developed the test scenarios.
 - The tests are easy to maintain, do the names of the variables make sense?
 - At the end of the test, you must send the postman project to the evaluator containing the scripts and the description of the covered scenarios.

## API's

```java
  [URL]: https://challenge-fielo-qa.herokuapp.com
  [APP_ID]: MPD4XHcIIGfMA0GCSqGSIbi232QKBgQCh7uxHjWd1CyRgPKiDb3DQEBAQUAA4GNADCB
```

- **/auth** [POST] - Endpoint responsible for the authorization of the application, it is necessary to add the key `x-app-id` with  `[APP_ID]` 
- **/heroes** [GET] - Endpoint responsible for returning all heroes.
- **/heroes** [POST] - Endpoint responsible for creating a new hero.
- **/heroes/battle** [POST]- Endpoint for battles between heroes.

## Authentication example
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
 
 ## Authentication Result
 
```java
{
    "auth": true,
    "token": "TOKEN_JWT"
}
```

## Example of data request
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
 
 ## API Documentation
 
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
 
Good Luck!
