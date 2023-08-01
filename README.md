
## Diablo 4 Class Comparison Microservice
Contribution by: Robert Afnani

Description: This microservice allows you to compare different classes in Diablo 4 and determine which class is best for solo play and which one is best for group play.

## How to Request Data
To request data from this microservice, make a POST request to the `/api/compare_classes` endpoint.  You should send a JSON payload with the following structure:

```json
{
    "classes": [
        {
            "class": "<class name>",
            "damage": <damage value>,
            "health": <health value>,
            "support_ability": <support ability value>
        },
        // Additional class objects can be added here
    ]
}

Here's an example of how to do this in Python using the requests library:
import requests

url = "http://localhost:5000/api/compare_classes"
data = {
    "classes": [
        {
            "class": "Necromancer",
            "damage": 80,
            "health": 70,
            "support_ability": 90
        },
        // Additional class objects can be added here
    ]
}
response = requests.post(url, json=data)

## How to Receive Data
The response from the microservice will be a JSON object with the following structure:

{
    "best_solo_class": {
        "class": "<class name>",
        "damage": <damage value>,
        "health": <health value>,
        "support_ability": <support ability value>
    },
    "best_group_class": {
        "class": "<class name>",
        "damage": <damage value>,
        "health": <health value>,
        "support_ability": <support ability value>
    }
}

You can parse this JSON object to get the data you need.  Here's how to do it in Python:
data = response.json()

best_solo_class = data["best_solo_class"]["class"]
best_group_class = data["best_group_class"]["class"]
