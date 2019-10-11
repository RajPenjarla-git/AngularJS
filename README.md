# AngularJS
AngularJS concepts overview

`AngularJS` is a **JavaScript framework**. It can be added to an HTML page with a <script> tag.
           
`<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>` 

**Or download angular.min.js file and save it in your project js folder**

###### AngularJS extends HTML with ng-directives.
***ng-app*** directive defines an AngularJS application.
***ng-model*** directive binds the value of HTML controls (input, select, textarea) to application data.
***ng-bind*** directive binds application data to the HTML view.
***ng-init*** directive initializes AngularJS application variables.
***ng-controller*** directive defines the controller.
***ng-repeat*** directive repeats an HTML element.
***ng-show*** directive shows the specified HTML element if the expression evaluates to true, otherwise the HTML element is hidden.
***ng-options*** directive in AngularJS is used to build and bind HTML element with options to a model property. 
It is used to specify `<options>` in a `<select>` list. It is designed specifically to populate the items of a dropdown list. It is supported by `<supported>` element.
***ngRoute*** module routes your application to different pages without reloading the entire application.
***ng-view*** is the directive that angular uses as a container to switch between views.


AngularJS expressions **{{ expression }}** bind AngularJS data to HTML the same way as the ng-bind directive.
         
## AngularJS Modules
       An AngularJS module defines an application. The module is a container for the different parts of an application. 
       The module is a container for the application controllers. Controllers always belong to a module.
       
### Creating a Module
A module is created by using the AngularJS function **angular.module**

**HTML:** `<div ng-app="myApp">`
**JS:** `
var app = angular.module('myApp', []);
`
### Adding a Controller   
Add a controller to your application, and refer to the controller with the **ng-controller** directive

**HTML:** `<div ng-app="myApp" ng-controller="myCtrl">`
**JS:** `
app.controller('myCtrl', function($scope) {
  $scope.firstName= "saRaj";
  $scope.lastName= "Penjarla";
});
`
## AngularJS Directives
AngularJS lets you extend HTML with new attributes called Directives.
AngularJS has a set of built-in directives which you can use to add functionality to your application.

### Create New Directives
New directives are created by using the ***.directive*** function.
we can use the module to create our own directives to our application.

When naming a directive, we must use a camel case name, saRajDirective, but when invoking it, we must use - separated name, sa-raj-directive

**HTML:**`<div ng-app="myApp" sa-raj-directive/>`
**JS:**`app.directive("saRajDirective", function() {
  return {
    template : "My Custom Directive"
  };
});`

we can invoke a directive by using: 
>1) Element name : `<sa-raj-directive></sa-raj-directive>`
>2) Attribute: `<div sa-raj-directive></div>` 
>3) Class: `<div class="sa-raj-directive"></div>` 
>4) Comment: `<!-- directive: sa-raj-directive -->`
### Restrictions
We can restrict our directives to only be invoked by some of the methods. Like, by adding a restrict property with the value **"A"**, the directive can only be invoked by **attributes**.

The legal restrict values are:

>**E** for Element name,
>**A** for Attribute,
>**C** for Class,
>**M** for Comment

`app.directive("saRajDirective", function() {
  return {
    restrict : "A",
    template : "<h1>Made by a directive!</h1>"
  };
});`

By default the value is **EA**. It means both Element and attribute names can invoke the directive.

## AngularJS Scope
The scope is the binding part between the HTML (view) and the JavaScript (controller).
When we make a controller in AngularJS, we pass the **$scope** object as an argument.
When adding properties to the **$scope** object in the controller, the view (HTML) gets access to these properties.

### Root Scope
All applications have a **$rootScope** which is the scope created on the HTML element that contains the ng-app directive.
The rootScope is available in the entire application.
If a variable has the same name in both the current scope and in the rootScope, the application uses the one in the current scope.

## AngularJS Filters
Filters can be added in AngularJS to format data. Filters can be added to expressions by using the pipe character **|**, followed by a filter.

AngularJS provides filters to transform data:

>1) currency: Format a number to a currency format.
>2) date: Format a date to a specified format.
>3) filter: Select a subset of items from an array.
>4) json: Format an object to a JSON string.
>5) limitTo: Limits an array/string, into a specified number of elements/characters.
>6) lowercase: Format a string to lower case.
>7) number: Format a number to a string.
>8) orderBy: Orders an array by an expression.
>9) uppercase: Format a string to upper case.

### Custom Filters
We can make our own filters by registering a new filter factory function with the module.

***myFormat*** custom filter will format every other character to uppercase.
` 
app.filter('myFormat', function() {
  return function(x) {
    var i, c, txt = "";
    for (i = 0; i < x.length; i++) {
      c = x[i];
      if (i % 2 == 0) {
        c = c.toUpperCase();
      }
      txt += c;
    }
    return txt;
  };
});
`
## AngularJS Services
A service is a function, or object, that is available for, and limited to, your AngularJS application.
AngularJS has about 30 built-in services. However, we can make our own service.

***$location*** service has methods which return information about the location of the current web page.
***$http*** service is one of the most common used services in AngularJS applications. The service makes a request to the server, and lets your application handle the response. **$http** is an AngularJS service for reading data from remote servers.
***$timeout*** service is AngularJS version of the **window.setTimeout** function.
***$interval*** service is AngularJS version of the **window.setInterval** function.

**Example:**`
app.controller('myCtrl', function($scope, $http) {
  $http.get("welcome.htm").then(function (response) {
    $scope.myWelcome = response.data;
  });
});
`
### Create Own Service
To create own service, connect service to the module.

`app.service('hexafy', function() {
  this.myFunc = function (x) {
    return x.toString(16);
  }
});
`

To use custom made service, we have to add it as a dependency when defining the controller.

**Example:** Use the custom made service named **hexafy** to convert a number into a hexadecimal number.

`app.controller('myCtrl', function($scope, hexafy) {
  $scope.hex = hexafy.myFunc(255);
});`

## AngularJS Routing
The **ngRoute** module helps our application to become a Single Page Application.

### What is Routing in AngularJS?
If you want to navigate to different pages in your application, but you also want the application to be a SPA (Single Page Application), with no page reloading, you can use the **ngRoute** module.

The ***ngRoute*** module routes your application to different pages without reloading the entire application.

### What do we Need?
To make our application ready for routing, we must include the AngularJS Route module:

`<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-route.js"></script>` 
**Or** download **angular.route.js** file and save it in our project js folder.

Then, we must add the **ngRoute** as a dependency in the application module: `var app = angular.module("myApp", ["ngRoute"]);`.
Use the **$routeProvider** to configure different routes in our application.
`
app.config(function($routeProvider) {
  $routeProvider
  .when("/", {
    templateUrl : "home.html"
  })
  .when("/contact", {
    templateUrl : "contact.html",
    controller : "contactCtrl"
  })
  .when("/about", {
    templateUrl : "about.html",
    controller : "aboutCtrl"
  });
});
`
### Controllers
With the $routeProvider you can also define a controller for each "view".

`
app.controller("contactCtrl", function ($scope) {
  $scope.msg = "Contact us at branch location";
});
app.controller("aboutCtrl", function ($scope) {
  $scope.msg = "It's a CMM5 Level MNC company";
});
`
### Where Does it Go?
Our application needs a container to put the content provided by the routing. 
**ng-view** directive is the container.

There are three different ways to include the **ng-view** directive in your application:
>1) `<div ng-view></div>`
>2) `<ng-view></ng-view>`
>3) `<div class="ng-view"></div>`

## AngularJS Routing Using UI-Router
The **UI-Router** is a routing framework for AngularJS built by the AngularUI team. 
It provides a different approach than ***ngRoute*** in that it changes your application views based on state of the application and not just the route URL.

