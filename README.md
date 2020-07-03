# curly
Standalone cURL library (single file, no dependencies)

<!-- MarkdownTOC autolink="true" autoanchor="true" levels="2,3" bracket="round" lowercase="only_ascii" -->

- [Requirements](#requirements)
- [Installation](#installation)
- [Sending request](#sending-request)
- [Receiving response](#receiving-response)
- [Custom options](#custom-options)
- [License](#license)

<!-- /MarkdownTOC -->

<a id="requirements"></a>
## Requirements
  - PHP 5.4 or newer



<a id="installation"></a>
## Installation

Download the file from [release page](https://github.com/esyede/curly) and drop to your project. That's it.

<a id="sending-request"></a>
## Sending request
Sekarang, mari kita coba membuat request sederhana menggunakan library `Curl` ini.

<a id="sending-a-get-request"></a>
#### Sending a GET request
Untuk membuat request bertipe `GET`, silahkan gunakan method `get()` seperti ini:

```php
$response = Curl::get('https://reqres.in/api/users?page=2');
```

<a id="sending-a-post-request"></a>
#### Sending a POST request
Untuk membuat request bertipe `POST`, silahkan gunakan method `post()` seperti ini:

```php
$parameters = $parameters = ['name' =>  'Danang', 'age' => 25];

$response = Curl::post('https://reqres.in/api/users', $parameters);
```


<a id="sending-a-put-request"></a>
#### Sending a PUT request

```php
$parameters = ['name' =>  'Agus', 'age' => 24];

$response = Curl::put('https://reqres.in/api/users', $parameters);
```


<a id="sending-a-delete-request"></a>
#### Sending a DELETE request

```php
$parameters = ['id' => 6];

$response = Curl::delete('https://reqres.in/api/users', $parameters);
```

<a id="download-file"></a>
#### Download file

```php
$target = 'https://github.com/esyede/eddie/archive/master.zip';
$destination = path('storage').'eddie.zip';

if (Curl::download($target, $destination)) {
	// Yay! it's downloaded!
}
```


<a id="receiving-response"></a>
## Receiving response
Every request will returns an `stdClass` object which has 2 properties:
  - `$header` that will contains the response headers.
  - `$body` that will contains the response body.

So, you can easily dump it to see what's inside:

```php
print_r($response->header);

print_r($response->body);
```

<a id="custom-options"></a>
## Custom options
You can also add or replace default options with your custom options like so:

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


<a id="license"></a>
## License

This library is licensed under the [MIT License](http://opensource.org/licenses/MIT)
