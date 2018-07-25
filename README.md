# Giga AI Resolver
*A Minimal PHP Resolver That Works!*

Resolver makes your code easier to read, remember and use. This standalone library is minimal & fast (~1.3KB) which you can use in any project, it uses PHP `ReflectionMethod` and `ReflectionFunction` feature.

## Use cases:

### Giga AI Framework
Giga AI framework uses resolver to help people define callback for a node easier. You don't need to remember the position of `$bot`, `$lead` and `$input` variable, you can use only variable you need. The callback is flexible, backward compatibility because we can add more variable later.

```php
$bot->answers('email', function ($bot, $lead, $input) {
	//
}); 
```

### LightKit
LightKit uses resolver to let people define their controllers with Laravel syntax.

```php
<?php

class SettingController extends Controller
{
	public function index()
	{
		// Method that doesn't have any argument.
	}

	public function create($request)
	{
		// Method that take $request argument
	}

	public function update($id, $request)
	{
		// $request argument can be in any position (in this case, second).
	}
}
```

## Usage
Resolve steps is easy: create an instance, bind data and resolve.

1. Create `$resolver` instance 
```php
$resolver = new GigaAI\Resolver\Resolver;
```

2. Bind [data] and resolve [method or function]
```
$resolver->bind([
	'id' => 1,
	'request' => $_REQUEST
])->resolve([$class, 'method']);

// or

$resolver->bind([
	'id' => 1,
	'request' => $_REQUEST
])->resolve('function_name');
```
