#### This file contains tests to evaluate that your bot behaves as expected.
#### If you want to learn more, please see the docs: https://rasa.com/docs/rasa/user-guide/testing-your-assistant/

## happy path
* greet: hello
  - utter_ask_location
* allergies: i want to test this intent and the entity [almonds](allergy)
  - utter
* location: i am from the city of [Madrid](city)
  - utter
