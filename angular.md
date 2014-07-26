---
title:  Expo AngularJS Style Guide
layout: default
---

Expo AngularJS Style Guide
==========================
*Abridged Edition*
View full version [here](https://github.com/mgechev/angularjs-style-guide).

File Naming
===========

Each JavaScript file should only hold a single component.
The file should be named with the component's name:

    module.controller('MyCtrl', ...  // Belongs in MyCtrl.js

Controllers are named UpperCamelCaseCtrl
----------------------------------------
The naming of the controller is done using the controller's functionality and adding `Ctrl` to the end.
Examples:
* HomePageCtrl
* ShoppingCartCtrl
* AdminPanelCtrl

Everything else is just lowerCamelCase
--------------------------------------
Modules, directives, filters, and services should be named with lowerCamelCase.

For indicating that module b is submodule of module a you can nest them by using namespacing like: a.b.

- - - - - - - - - - - -

Place attribute directives at the end of the element, after normal attributes:

✓ RIGHT

    <input class="ipt" type="text" placeholder="name" require ng-model="user.name">

✗ WRONG

    <input ng-model="user.name" class="ipt" type="text" placeholder="name" require>
    <input class="ipt" ng-model="user.name" type="text" placeholder="name" require>

- - - - - - - - - - - -

Use Angular's wrapers:

* `$timeout` instead of `setTimeout`
* `$interval` instead of `setInterval`
* `$window` instead of `window`
* `$document` instead of `document`
* `$http` instead of `$.ajax`

Use `$resource` instead of `$http` when possible.
The higher level of abstraction will save you from redundancy.

- - - - - - - - - - - -

When resolving dependencies through the DI mechanism of AngularJS, sort the dependencies by their type - the built-in AngularJS dependencies should be first, followed by your custom ones:

    module.factory('Service', function ($rootScope, $timeout, MyCustomDependency1, MyCustomDependency2) {
      return {
        //Something
      };
    });

- - - - - - - - - - - -

Use the original names of the controller's dependencies. This will help you produce more readable code:
✓ RIGHT
-------
    module.controller('MyCtrl', ['$scope', function ($scope) {
      //...body
    }]);

✗ WRONG
-------
    module.controller('MyCtrl', ['$scope', function (s) {
      //...body
    }]);
