#### This file contains tests to evaluate that your bot behaves as expected.
#### If you want to learn more, please see the docs: https://rasa.com/docs/rasa/user-guide/testing-your-assistant/

## happy path
* greet: hello
  - utter_greet
  - utter_ask_location
* location: i am from the city of [Madrid](city)
  - utter_allergies
* allergies: i can't have [almonds](allergy)
  - utter_restaurant

## happy path no allergy
* greet: hello
  - utter_greet
  - utter_ask_location
* location: i live in [Barcelona](city)
  - utter_allergies
* deny: no
  - utter_restaurant_no_allergy

## sad path no city
* greet: hello
  - utter_greet
  - utter_ask_location
* deny: i don't want to
  - utter_restaurant_no_location
