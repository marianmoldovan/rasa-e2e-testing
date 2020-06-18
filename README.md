# rasa-e2e-testing

This project contains a guide as a introduction to testing using RASA

The demo project it's a simple restaurant bot, the happy path it's the following:

User: hello
Bot: Welcome to my restaurant, I will recommend the best place to eat. Where do you live?
User: Madrid
Bot: Any allergies I should know about?
User: I am allergic to almonds
Bot: The best restaurant for a almonds intolerant in Madrid is Vega, best vegan restaurant in town
User: thanx
Bot: Goodbye

Take a look at the stories.md and domain.yml to understand the features built


## Dependencies

You will need to have installed docker and to have a terminal where to run commands. To install Docker, check the [official docs](https://docs.docker.com/get-docker/)


## How to test

You need to add .md files in the **tests** folder. Rasa will detect automatically the files, and you will just need to run the test command. There is a sample test there called, hello_unit_tests.md containing:

```
## say hello
* greet: hello
  - utter_greet
```

Let's see what it means:

```
## say hello - title of the test
* greet -> intent expected to be predicted: hello -> text that we want to test that matches the left assignment intent
  - utter_greet -> action expecteded to be triggered
```

You can also chain intents, just as writting stories, for example:

```
## happy path
* greet: hello
  - utter_ask_location
* allergies: i want to test this intent and the entity [almonds](allergy)
  - utter
```

Here we chain the greet and allergies intents. Also, expect that the value [almonds] to be detected as an (allergy) entity.

In order to test you need to use the following command:

`docker run -it -v $(pwd):/app rasa/rasa:1.10.3-full test`

The results of the test are gonna be extracted to the **results** folder.

If you want to test manually the bot, run: `docker run -it -v $(pwd):/app rasa/rasa:1.10.3-full shell`

## Task

Write the following tests for our restaurant bot

## Test 1

Check that when an user says **Hello**, the bot asks the user where he lives.

## Test 2

Check that when an user says **good bye**, the bot also says good bye

## Test 3

Test the happy path. Create a tests where the user says **Hello**, afterwards, indicates the city where he lives (a spanish one) and finally that he is allergic to the seafood. The expected response is a restaurant recommendation.

## Extra test 1

Test the path where the user initiates the interaction with a **Hello**, says the city he is from, but doesn't specify any allergy. The expected response should be a restaurant recommendation, without any allergy.

## Extra test 2

Test the path where the user initiates the interaction with a **Hello**, but says no city or allergy. The response he should get contains no recommendation.

### Other commands

Train bot `docker run -v $(pwd):/app rasa/rasa:1.10.3-full train --domain domain.yml --data data --out models`
