Build a Telephone Number Validator
In the US, phone numbers can be formatted in many ways. Here are some examples of valid formats for US phone numbers:

1 555-555-5555
1 (555) 555-5555
1(555)555-5555
1 555 555 5555
5555555555
555-555-5555
(555)555-5555
Note that the area code is required. Also, if the country code is provided, you must confirm that the country code is 1.

Objective: Build an app that is functionally similar to https://telephone-number-validator.freecodecamp.rocks

User Stories:

You should have an input element with an id of "user-input"
You should have a button element with an id of "check-btn
You should have a button element with an id of "clear-btn"
You should have a div element with an id of "results-div"
When you click on the #check-btn element without entering a value into the #user-input element, an alert should appear with the text "Please provide a phone number"
When you click on the #clear-btn element, the content within the #results-div element should be removed
When the #user-input element contains 1 555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 555-555-5555"
When the #user-input element contains 1 (555) 555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 (555) 555-5555"
When the #user-input element contains 5555555555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 5555555555"
When the #user-input element contains 555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text `"Valid US number: 555-555-5555"
When the #user-input element contains (555)555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: (555)555-5555"
When the #user-input element contains 1(555)555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1(555)555-5555"
When the #user-input element contains 555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 555-5555"
When the #user-input element contains 5555555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 5555555"
When the #user-input element contains 1 555)555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 1 555)555-5555"
When the #user-input element contains 1 555 555 5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 555 555 5555"
When the #user-input element contains 1 456 789 4444 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 456 789 4444"
When #user-input contains 123**&!!asdf# and #check-btn is clicked, #results-div should contain the text "Invalid US number: 123**&!!asdf#"
When the #user-input element contains 55555555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 55555555"
When the #user-input element contains (6054756961) and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: (6054756961)"
When the #user-input element contains 2 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2 (757) 622-7382"
When the #user-input element contains 0 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 0 (757) 622-7382"
When the #user-input element contains -1 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: -1 (757) 622-7382"
When the #user-input element contains 2 757 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2 757 622-7382"
When the #user-input element contains 10 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 10 (757) 622-7382"
When the #user-input element contains 27576227382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 27576227382"
When the #user-input element contains (275)76227382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: (275)76227382"
When the #user-input element contains 2(757)6227382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2(757)6227382"
When the #user-input element contains 2(757)622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2(757)622-7382"
When the #user-input element contains 555)-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 555)-555-5555"
When the #user-input element contains (555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: (555-555-5555"
When #user-input contains (555)5(55?)-5555 and #check-btn is clicked, #results-div should contain the text "Invalid US number: (555)5(55?)-5555"
When the #user-input element contains 55 55-55-555-5 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 55 55-55-555-5"
When the #user-input element contains 11 555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 11 555-555-5555"
Fulfill the user stories and pass all the tests below to complete this project. Give it your own personal style. Happy Coding!

Run the Tests (Ctrl + Enter)
Save your Code
Reset this lesson
Get Help
Tests
Failed:You should have an input element with an id of "user-input".
Failed:You should have a button element with an id of "check-btn".
Failed:You should have a button element with an id of "clear-btn".
Failed:You should have a div element with an id of "results-div".
Failed:When you click on the #check-btn element without entering a value into the #user-input element, an alert should appear with the text "Please provide a phone number".
Failed:When you click on the #clear-btn element, the content within the #results-div element should be removed.
Failed:When the #user-input element contains 1 555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 555-555-5555".
Failed:When the #user-input element contains 1 (555) 555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 (555) 555-5555".
Failed:When the #user-input element contains 5555555555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 5555555555".
Failed:When the #user-input element contains 555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 555-555-5555".
Failed:When the #user-input element contains (555)555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: (555)555-5555".
Failed:When the #user-input element contains 1(555)555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1(555)555-5555".
Failed:When the #user-input element contains 555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 555-5555".
Failed:When the #user-input element contains 5555555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 5555555".
Failed:When the #user-input element contains 1 555)555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 1 555)555-5555".
Failed:When the #user-input element contains 1 555 555 5555 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 555 555 5555".
Failed:When the #user-input element contains 1 456 789 4444 and the #check-btn element is clicked, the #results-div element should contain the text "Valid US number: 1 456 789 4444".
Failed:When #user-input contains 123**&!!asdf# and #check-btn is clicked, #results-div should contain the text "Invalid US number: 123**&!!asdf#".
Failed:When the #user-input element contains 55555555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 55555555".
Failed:When the #user-input element contains (6054756961) and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: (6054756961)".
Failed:When the #user-input element contains 2 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2 (757) 622-7382".
Failed:When the #user-input element contains 0 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 0 (757) 622-7382".
Failed:When the #user-input element contains -1 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: -1 (757) 622-7382".
Failed:When the #user-input element contains 2 757 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2 757 622-7382".
Failed:When the #user-input element contains 10 (757) 622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 10 (757) 622-7382".
Failed:When the #user-input element contains 27576227382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 27576227382".
Failed:When the #user-input element contains (275)76227382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: (275)76227382".
Failed:When the #user-input element contains 2(757)6227382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2(757)6227382".
Failed:When the #user-input element contains 2(757)622-7382 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 2(757)622-7382".
Failed:When the #user-input element contains 555)-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 555)-555-5555".
Failed:When the #user-input element contains (555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: (555-555-5555".
Failed:When #user-input contains (555)5(55?)-5555 and #check-btn is clicked, #results-div should contain the text "Invalid US number: (555)5(55?)-5555".
Failed:When the #user-input element contains 55 55-55-555-5 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 55 55-55-555-5".
Failed:When the #user-input element contains 11 555-555-5555 and the #check-btn element is clicked, the #results-div element should contain the text "Invalid US number: 11 555-555-5555".