## time path
* greet
  - utter_greet
  - utter_wh_person

## inform
* inform_person{"person":"Vlad Maraev"}
  - utter_yn_correct
* affirm OR thankyou
  - utter_wh_date
* inform_date{"date":"Monday"}
  - utter_yn_correct
* affirm OR thankyou
  - utter_wh_time
* inform_time{"time":"Nine"}
  - utter_yn_correct
* affirm OR thankyou
  - utter_inform
  - utter_bye
  
## incorrect
* deny
  - slot{"person": null}
  - slot{"date": null}
  - slot{"time": null}
  - utter_bye

