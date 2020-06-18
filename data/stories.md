## happy path
* greet
  - utter_greet
  - utter_ask_location
* location
  - utter_allergies
* allergies
  - utter_restaurant
  - slot{"city": null}
  - slot{"allergy": null}   

## happy path no allergy
* greet
  - utter_greet
  - utter_ask_location
* location
  - utter_allergies
* deny
  - utter_restaurant_no_allergy
  - slot{"city": null}

## path with no location and no allergy
* greet
  - utter_greet
  - utter_ask_location
* deny
  - utter_restaurant_no_location

## goodbye
* goodbye OR deny
  - utter_goodbye
