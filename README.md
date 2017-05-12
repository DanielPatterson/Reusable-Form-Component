# Reusable-Form-Component
Creating a reusable form component with angular js


#### Dependencies:
- angular.min.js

#### Form:

&lt;form name="myForm" novalidate&gt;
    &lt;form-input&gt;&lt;/form-input&gt;
    &lt;button type="submit" ng-disabled="myForm.name.$invalid"&gt;submit&lt;/button&gt;
&lt;/form&gt;

#### input-field.html:

&lt;div ng-repeat="data in $ctrl.inputs"&gt;
  &lt;label&gt;{{data.label}}&lt;/label&gt;
  &lt;input type="{{data.type}}" name="name" ng-model="name" placeholder="{{data.placeholder}}" required /&gt;
&lt;/div&gt;

#### Angular js:

```` javascript
angular.module('myApp', [
'formInput'
]);

angular.module('formInput', []);

angular.module('formInput').component('formInput', {
	
    templateUrl: 'input-field.html',
    controller: ['$http',
      function formInputController($http) {
        var self = this;

        $http.get('inputs.json').then(function(response) {
          self.inputs = response.data;
        });
      }
    ]
	
});
````

#### inputs.json:

```` json
[
  {
    "label": "First name",
	"type": "text",
	"name": "fname",
	"placeholder": "your first name"
  },
  
  {
    "label": "Last name",
	"type": "text",
	"name": "lname",
	"placeholder": "your last name"
  },
  
  {
    "label": "email",
	"type": "email",
	"name": "email",
	"placeholder": "your email address"
  },
  
  {
    "label": "phone",
	"type": "text",
	"name": "phone",
	"placeholder": "your phone number"
  }
]
````
