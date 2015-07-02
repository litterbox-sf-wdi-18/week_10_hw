# Week 10 
## API's and Angular

The objective of this assignment is to finish the design of an API that uses basic http sign up and createes a unique token that can be used to confirm the users interactions with the API.

## App 

You'll need everything from the point of sale application you developed during the week. You should finish this if you haven't already. If you need pointers. See the `setup_help.md` file included in this repository. Once you have a simple receipts API you that a user can sign up and login to using an email and passowrd you should build an angular application for the `/account` page. The account page should be an angular application that satisfies the following user stories:

* User can see a dashboard of their profile information. User can edit profile details without page reload via modal -- "medium/difficult".
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

Then verify that in your `vendor/assets/components/` their is an `angular` folder. If you verify that you application has angular you can then move on to requiring it in your assets.

`app/assets/javascripts/application.js`

```javascript
//= require jquery
//= require jquery_ujs
//= require turbolinks
//= require angular/angular 
//= require_tree .

```

Do you see angular in the above list of requires. It's important that it comes before `//= require_tree .`


Now you can write all you angular application code in your application.js. Let's add some simple logic to our application.js.

`application.js`

```javascript
...

var AccountApp = angular.module("AccountApp", [])

AccountApp.controller("MainCtrl", function ($scope) {
	$scope.greeting = "Hello world";
});

```

Then in your `show.html.erb` for your `/account` route. let's add the following.

```html

<div ng-app="AccountApp">
	<div ng-controller="MainCtrl">
		{{greeting}}
	</div>
</div>

```

Then if you login and go to your account at [localhost:3000/account](localhost:3000/account).

You should see 

```
Hello world
```


## Displaying User Data

You can get information about the user using angular's built-in `$http` module.


`application.js`

```
var AccountApp = angular.module("AccountApp", [])

AccountApp.controller("MainCtrl", function ($scope, $http) {
	$scope.greeting = "Hello world";
	
	$scope.current_user = null;
	
	$http.get("/account.json").
		success(function (data) {
			$scope.current_user = data;
		});
});

```



This assumes you have the following route


```ruby

get "/account", to: "store_owners#show"
```

with a `show` method that looks something like th following.



```ruby

def show
  @store_owner = current_owner
  
  respond_to do |f|
  	f.html
  	f.json {render json: @store_owner }
  end
end

```

This just glorified version of the `users#show` that we've worked with the whole class.


You can then display the user information on the in the `show.html.erb`.


```html
<div ng-app="AccountApp">
	<div ng-controller="MainCtrl">
		{{greeting}}
		{{current_user}}
	</div>
</div>

```

## Pitfalls: 422 Unprocessible

If you're going to be posting and patching to the rails server you'll need a csrf param. Angular has to be congifured to send this with a request.

`application.js`

```javascript

var AccountApp = angular.module("AccountApp", [])

// just add this!! 
AccountApp.config(["$httpProvider", function ($httpProvider) {
	$httpProvider.
		defaults.headers.common["X-CSRF"] = $("meta[name=csrf-token]").attr("content");
}])

AccountApp.controller("MainCtrl", function ($scope, $http) {
	$scope.greeting = "Hello world";
	
	$scope.current_user = null;
	
	$http.get("/account.json").
		success(function (data) {
			$scope.current_user = data;
		});
});

```















