Proxy Checker Laravel Version: 0.2 
==========================

Service Provider for Proxy Checking (type - http, socks4, socks5) that returns all the necessary information related to each proxy(s) for Laravel PHP Framework [ [Packagist] ]

[Packagist]: <https://packagist.org/packages/sahusoftcom/proxy-checker>

## Installation

Type the following command in your project directory

`composer require sahusoftcom/proxy-checker`

OR

Add the following line to the `require` section of `composer.json`:

```json
{
    "require": {
        "sahusoftcom/proxy-checker": "dev-master"
    }
}
```

## Setup

In `/config/app.php`, add the following to `providers`:
  
```php
SahusoftCom\ProxyChecker\ProxyCheckerServiceProvider::class
```

## How to use

1. You should use the class `SahusoftCom\ProxyChecker\ProxyCheckerService`
2. Pass `$url` & `$config` parameter in `ProxyCheckerService` class

	```php
		/*
		*	$config [optional]
		*/
		$config = [
			'timeout'   => 100,
			'check'     => ['get', 'post', 'cookie', 'referer', 'user_agent'],
		    ];

		/*
		*	$url [required1]
		*/
		$url = "https://www.google.com";
		
		$proxies = [
			'XXX.XXX.XXX.XXX:XXXX,username:password,Socks4',
			'XXX.XXX.XXX.XXX:XXXX,username:password,Socks5',
			'XXX.XXX.XXX.XXX:XXXX'
		];

		$proxyCheckObject = new ProxyCheckerService($url, $config);
		$result = $proxyCheckObject->checkProxies($proxies);

		echo "<pre>";
		print_r($result);
		echo "</pre>";
	```

 ## Sample Output
 
 ```
Array
	(
		[XXX.XXX.XXX.XXX:XXXX,username:password] => Array
			(
				[allowed] => Array
					(
					)

				[disallowed] => Array
					(
						[0] => get
						[1] => post
						[2] => cookie
						[3] => referer
						[4] => user_agent
					)

				[proxy_level] => 
				[info] => Array
					(
						[url] => https://www.google.com/
						[content_type] => text/html; charset=UTF-8
						[http_code] => 200
						[header_size] => 1070
						[request_size] => 418
						[filetime] => -1
						[ssl_verify_result] => 0
						[redirect_count] => 0
						[total_time] => 2.055918
						[namelookup_time] => 0.007662
						[connect_time] => 0.313878
						[pretransfer_time] => 1.490388
						[size_upload] => 0
						[size_download] => 11431
						[speed_download] => 5560
						[speed_upload] => 0
						[download_content_length] => -1
						[upload_content_length] => -1
						[starttransfer_time] => 1.758965
						[redirect_time] => 0
						[redirect_url] => 
						[primary_ip] => XXX.XXX.XXX.XXX
						[certinfo] => Array
							(
							)

						[primary_port] => 8080
						[local_ip] => XXX.XXX.X.XXX
						[local_port] => XXXXX
					)

			)

	)
```
