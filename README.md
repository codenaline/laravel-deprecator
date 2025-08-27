# Laravel Deprecated Detector

Laravel Deprecated Detector is a lightweight middleware package that automatically scans controller methods for `@deprecated` annotations in their PHPDoc and adds an `X-Deprecated` header to the HTTP response. This helps frontend clients and API consumers identify deprecated endpoints and adjust accordingly.

## 🚀 Features

- Detects deprecated controller methods using PHPDoc `@deprecated`
- Adds `X-Deprecated` header to HTTP responses
- Plug-and-play middleware for Laravel applications
- Supports Laravel 8 and above
- Designed for extensibility (e.g. future support for PHP 8+ attributes)

## 📦 Installation

```bash
composer require mahdi/laravel-deprecated-detector
```

## ⚙️ Setup
The package auto-registers its middleware into the web middleware group. If needed, you can manually register the service provider:

```php
// config/app.php

'providers' => [
    Mahdi\DeprecatedDetector\Providers\DeprecatedServiceProvider::class,
],
```
## 🧪 Usage
Simply annotate any controller method with @deprecated in its PHPDoc:

```php
/**
 * @deprecated This endpoint will be removed in v2.0. Use `newMethod()` instead.
 */
public function oldMethod()
{
    // ...
}
```

When this method is called, the response will include:

```Code
X-Deprecated: true.
X-Deprecated-Message: This endpoint will be removed in v2.0. Use `newMethod()` instead.
```
## 🔧 Configuration
You can publish the config file to customize behavior (coming soon):

```bash
php artisan vendor:publish --tag=deprecated-config
```

## 🛠️ Roadmap
[ ] Support for PHP 8+ `#[Deprecated] attributes`

[ ] Logging deprecated calls

[ ] Slack/Sentry integration for deprecated usage alerts

[ ] Configurable header name and message format

## 🤝 Contributing
Pull requests are welcome! If you have ideas for improvements or would like to report a bug, please feel free to open an issue.


## 👨🏻‍💻 Credits

- [Mahdi Rezaei](https://github.com/mahdirezaei-dev)

## 📄 License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
