This code allows to use .Json locale files as nested attributes with laravel functionalities (variables, countable).

# Usage

`resources/lang/en.json`
```json
{
	"messages" :{
		"welcome": "Welcome to my website"
	},
	"user": {
		"greet": "Hi, :Name",
		"arrived": "You have arrived in :CITY"
	},
	"models": {
		"products": {
			"car": ":count car|:count cars",
			"apple": "{1} an apple|{2} two apples|{3,*} many apples"
		}
	}
}
```

##### Basic use
```php
__('messages.welcome'),
// OUTPUT: 'Welcome to my website'
```
##### Variable usage
```php
// Variable usage
__('user.greet', ['name' => 'david']),
// OUTPUT: 'Hi, David'

__('user.arrived', ['city' => 'chicago']),
// OUTPUT: 'You have arrived in CHICAGO'
```
##### Countable usage
```php
trans_choice('models.products.car', 1),
// OUTPUT: '1 car'

trans_choice('models.products.car', 8),
// OUTPUT: '8 cars'

trans_choice('models.products.apple', 3));
// OUTPUT: 'many apples'
```

# Configuration
you must load `bootstrap/helpers.php` before the laravel auto loader, to archive this, add this line  to your `public/index.php` file: 

```php

/*
|--------------------------------------------------------------------------
| Check If The Application Is Under Maintenance
|--------------------------------------------------------------------------
*/

// ...

/*
|--------------------------------------------------------------------------
| Register Custom Helpers
|------------------------------------------------------------------------
*/

require __DIR__.'/../bootstrap/helpers.php';

/*
|--------------------------------------------------------------------------
| Register The Auto Loader
|--------------------------------------------------------------------------
*/

// ...
```
