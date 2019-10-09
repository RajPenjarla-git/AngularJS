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
         
**HTML:** `<div ng-app="myApp" ng-controller="myCtrl">`

**JS:**`
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.firstName= "John";
  $scope.lastName= "Doe";
});
`
