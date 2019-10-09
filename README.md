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
### Adding a Directive
AngularJS has a set of built-in directives which you can use to add functionality to your application.
However, we can use the module to create our own directives to our application.

**HTML:**`<div ng-app="myApp" sa-raj-directive/>`
**JS:**`app.directive("saRajDirective", function() {
  return {
    template : "My Custom Directive"
  };
});
