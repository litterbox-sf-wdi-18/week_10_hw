# Week 10 
## API's and Angular

The objective of this assignment is to finish the design of an API that uses basic http sign up and creates a unique token that can be used to confirm a user's interactions with the API.

## Brief

You'll need to reference the point of sale application you developed during the week. You should finish this if you haven't already. If you need help, see the `setup_help.md` file included in this repository. Once you have a simple receipts API you, where a user can sign up and login with an email and password, then focus on the angular application for the `/account` page. This page should contain an angular application that satisfies the following.

###User stories

User can...

* View reset their api token without page reload -- "simple"
* Click a button to view all their `simple_receipts` without page reload -- "simple".
* See a form that allows them to add a `simple_receipt` without page reload -- "medium".
* See the new `simple_receipt` added to the page.
* See how many receipts were created today -- "easy/medium depending on approach".
* Delete a receipt without page reload -- "medium".
* Click a receipt and see a model to edit and update  it without changing views -- "medium/difficult".
* See a dashboard of their profile information. User can edit profile details without page reload via modal -- "medium/difficult".
* See how see a total from all receipts for the day -- "easy/medium/hard depending on your approach".

(complete these in whatever order you wish)

## Note

You can build the `/account` application with jQuery if you don't feel comfortable with angular, but this is in some ways more difficult; however, it's a great exercise if won't use angular in the final project.

## Getting Started: Angular and Rails


Let's install Angular with Rails. Let's just do this with Bower.

```
npm install -g bower
```

Once you have Bower you can get started. However, we don't want our bower_components in any folder. Let's make sure they end up `vendor/assets/`



```bash
touch .bowerrc

```

And in the `.bowerrc`


```javascript
{
	"directory": "vendor/assets/components"
}

```

Then we can install via bower angular.


```
bower install --save angular
```

Then verify that in your `vendor/assets/components/` their is an `angular` folder. If you verify that you application has angular.
