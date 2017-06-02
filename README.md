# pingpong-championship
A Chanmpionship API for PingPong at Neemu

## Installation
Start the PingPong API installing requirements
```sh
$ pip install -r requirements.txt
```

## Start API
```sh
$ uwsgi --yaml config.yml
```

## How to Use
You can use *curl* to test the API. All requests returns a json string

Starts creating a new Championship. You need to name it.

### Create a new Championship
```sh
$ curl -X POST localhost:9000/championship/create/ --data "{\"name\":\"Test\"}"
```
It will return:
```json
{
    "status": "ok",
    "data": {
        key": "abc123"
    }
}
```

### View all Championships
```sh
$ curl -X GET localhost:9000/championship/
```
It will return:
```json
{
    "status": "ok",
    "data": {
        "championships": [
            "abc123",
            "123456"
        ]
    }
}
```

### View a specific Championships
```sh
$ curl -X GET localhost:9000/championship?key=abc123
```
It will return:
```json
{
    "status": "ok",
    "data": {
        "championship": [
            "abc123": {
                "players": {
                    "qty": 30,
                    "names": ["A", "B"],
                }
                "steps": {
                    "1-official": {
                        "playersQty": 19,
                        "matchesQty": 4,
                        "matches": [
                            {
                                "key": "abc123-match-1",
                                "team-1": {
                                    "players": [
                                        "A",
                                        "B"
                                    ],
                                    "score": 5
                                }
                                "team-2": {
                                    "players": [
                                        "C",
                                        "D"
                                    ],
                                    "score": 7
                                }
                                "winner": "team-1"
                            }
                        ]
                    },
                    "1-recapture": {
                        "playersQty": 19,
                        "matchesQty": 4,
                        "matches": [
                            {
                                "key": "abc123-match-1",
                                "team-1": {
                                    "players": [
                                        "A",
                                        "B"
                                    ],
                                    "score": 5
                                }
                                "team-2": {
                                    "players": [
                                        "C",
                                        "D"
                                    ],
                                    "score": 7
                                }
                                "winner": "team-1"
                            }
                        ]
                    }
                }
            }
        ]
    }
}
```

### Add a player
```sh
$ curl -X POST localhost:9000/championship/addPlayer/ --data "{championshipKey, name, gender, age, urlImage}"
```
