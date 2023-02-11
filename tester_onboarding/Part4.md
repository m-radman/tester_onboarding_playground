# Part 4: UI Testing Intro (before getting into coding)

### Application under test → [https://the-internet.herokuapp.com/](https://the-internet.herokuapp.com/)

### **Writing down test for [Basic Auth](https://the-internet.herokuapp.com/basic_auth) feature** 

- Title: `basic auth happy path  test`  
  - Test Steps:   
    - go to url "https://the-internet.herokuapp.com/basic_auth"
    - expect alert box to be in viewport
    - input valid credentials username "admin" and  password "admin"
    - click "Sign in" button
    - expect to see text strictly equal to "Congratulations! You must have the proper credentials."

### Note on Gherkin Syntax (Given When Then) 

Same test written using GIVEN WHEN THEN (cucumber’s [Gherkin syntax](https://cucumber.io/docs/gherkin/reference/))

**Writing down test for [Basic Auth](https://the-internet.herokuapp.com/basic_auth) feature with Gherkin** 

- Executable specification written  in Gherkin:  
  ```gherkin
  Feature: Basic Auth

    # Basic Auth happy path example  
    Scenario: Pass Basic Auth Successfully 
      Given that user navigated to "https://the-internet.herokuapp.com/basic_auth"
      When user inputs username "admin"
      And user inputs password "admin"
      And user clicks on "Sing in" button
      Then user is successfully loged in
      And user is presented with "Congratulations!" message
  ```

#### An actual implementation of the test script 

- An outline of the actual test file (using Jest testing framework in JavaScript): 
  ```jsx
  describe("test basic auth", function() {
    it("expect auth to be success for valid credentials", async function() {
      // step1 go to url "https://the-internet.herokuapp.com/basic_auth"
      // selenium_fn_that_knows_how_to_navigate_to_url(url) 
      // wait to see smth on screen / wait for go to url to take effect 
      // step2 input valid credentials username "admin" and  password "admin"
      // step3 click "Sign in" button 
      // selenium_fn_that_knows_to_click_on_smth()
      // step4 EXPECT to see text strictly equal to "Congratulations! You must have the proper credentials."
    })
  })
  ```

#### **Writing down test for [Add/Remove Elements](https://the-internet.herokuapp.com/add_remove_elements/) feature**

- Title: `add element happy path  test`
  - Test Steps: 
    - go to url "[https://the-internet.herokuapp.com/basic_auth](https://the-internet.herokuapp.com/add_remove_elements/)"
    - expect   “Add element” button to be in viewport
    - click “Add element” button
    - expect new “Delete” button to become present in DOM
    - click “Add element” button once more
    - expect two “Delete” button elements to be present in DOM at this point
    - click “Delete” button
    - expect one “Delete” button element to be in viewport
    - click “Delete” button
    - expect no “Delete” buttons in viewport

> to be present in DOM ≠ to be in viewport   
> to be visible on screen (not hidden) == to be in viewport   

#### **Writing down test for validating content in nested frames** 

-  Title: `switch context to LEFT frame`  
  - Test Steps:   
    - go to url [https://the-internet.herokuapp.com/nested_frames](https://the-internet.herokuapp.com/nested_frames)
    - expect `top-frame` to be in DOM
    - switch context to `top-frame`
    - expect `left-frame` to be in DOM
    - switch context to `left-frame`
    - get text from `body` of the embedded html document and expect it to be equal to “LEFT”
    - switch context back to root html document

- Title: `switch context to BOTTOM frame`  
  - Test Steps:   
    - go to url [https://the-internet.herokuapp.com/nested_frames](https://the-internet.herokuapp.com/nested_frames)
    - expect `bottom-frame` to be in DOM
    - switch context to `bottom-frame`
    - get text from `body` of the embedded html document and expect it to be equal to “BOTTOM”
    - switch context back to root html document

--- 

:point_left: [go back to main page](../README.md)