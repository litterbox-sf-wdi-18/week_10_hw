# Week 10 
## API's and Angular

The objective of this assignment is to finish the design of an API that uses basic http sign up and createes a unique token that can be used to confirm the users interactions with the API.

## App 

You'll need everything from the point of sale application you developed during the week. You should finish this if you haven't already. If you need pointers. See the `setup_help.md` file included in this repository. Once you have a simple receipts API you that a user can sign up and login to using an email and passowrd you should build an angular application for the `/account` page. The account page should be an angular application that satisfies the following user stories:

* User see a dashboard of their profile information. User can edit profile details without page reload via modal -- "medium/difficult".
* User can view reset their api token without page reload -- "simple"
* User can click a button to view all their `simple_receipts` without page reload -- "simple".
* User can see a form that allows them to add a `simple_receipt` without page reload -- "medium".
  * User can see the new `simple_receipt` added to the page.
* User can delete a receipt without page reload -- "medium".
* User can click a receipt and see a model to edit and update  it without changing views -- "medium/difficult".
* User can see how many receipts were created today -- "easy/medium depending on approach".
* User can see how see a total from all receipts for the day -- "easy/medium/hard depending on your approach".


## Note

You can build the `/account` application with jQuery if you don't feel comfortable with angular, but this will make everything more difficult. It's a good exercise if you know you won't use angular on your final project.

