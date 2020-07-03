# curly
Standalone cURL library (single file, no dependencies)



### Requirements
  - PHP 5.4 or newer




### Installation
Download the file from [release page](https://github.com/esyede/curly/releases) and drop to your project. That's it.




### Sending request
Now, let's try sending simple request using this library:


**Sending a GET request:**
```php
$response = Curl::get('https://reqres.in/api/users?page=2');
```


**Sending a POST request:**
```php
$parameters = $parameters = ['name' =>  'Danang', 'age' => 25];

$response = Curl::post('https://reqres.in/api/users', $parameters);
```


**Sending a PUT request:**
```php
$parameters = ['name' =>  'Agus', 'age' => 24];

$response = Curl::put('https://reqres.in/api/users', $parameters);
```


**Sending a DELETE request:**
```php
$parameters = ['id' => 6];

$response = Curl::delete('https://reqres.in/api/users', $parameters);
```


**Downloading file:**
```php
$target = 'https://github.com/esyede/eddie/archive/master.zip';
$destination = path('storage').'eddie.zip';

if (Curl::download($target, $destination)) {
	// Yay! it's downloaded!
}
```



### Receiving response
Every request will returns an `stdClass` object which has 2 properties:
  - `$header` that will contains the response headers.
  - `$body` that will contains the response body.

So, you can easily dump it to see what's inside:
```php
print_r($response->header);

print_r($response->body);
```



### Custom options
You can also add or replace default options with your custom options. For example, let's change the http header and redirection option:
```php
$parameters =[];

$custom_options = [
	CURLOPT_FOLLOWLOCATION => true,
	CURLOPT_HTTPHEADER => [
		'Cache-Control: no-cache',
		'Accept-Encoding: gzip, deflate',
		'Accept-Language: en-US,en;q=0.5',
	],
];

$response = Curly::get('https://foobar.com', $parameters, $custom_options);
```

List of supported options is available on the [PHP cURL documentation](https://www.php.net/manual/en/function.curl-setopt.php).

That pretty much it. Thank you for stopping by!



### License
This library is licensed under the [MIT License](http://opensource.org/licenses/MIT)
