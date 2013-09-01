[![Build Status](https://travis-ci.org/thomaswelton/laravel-gravatar.png?branch=master)](https://travis-ci.org/thomaswelton/laravel-gravatar)
[![Latest Stable Version](https://poser.pugx.org/thomaswelton/laravel-gravatar/v/stable.png)](https://packagist.org/packages/thomaswelton/laravel-gravatar)
[![Total Downloads](https://poser.pugx.org/thomaswelton/laravel-gravatar/downloads.png)](https://packagist.org/packages/thomaswelton/laravel-gravatar)

## Installation

Update your `composer.json` file to include this package as a dependency
```json
"thomaswelton/laravel-gravatar": "dev-master"
```

Register the Gravatar service provider by adding it to the providers array in the `app/config/app.php` file.
```
Thomaswelton\LaravelGravatar\LaravelGravatarServiceProvider
```

Alias the Gravatar facade by adding it to the aliases array in the `app/config/app.php` file.
```php
'aliases' => array(
	'Gravatar' => 'Thomaswelton\LaravelGravatar\Facades\Gravatar'
)
```

## Configuration - Optional

Copy the config file into your project by running
```
php artisan config:publish thomaswelton/laravel-gravatar
```

Update the config file to specify the default avatar size to use.
And a default image to be return if no Gravatar is found allowed defaults
- (bool)   false
- (string) 404
- (string) mm
- (string) identicon
- (string) monsterid
- (string) wavatar
- (string) retro

## Usage

### Gravatar::src($email, $size = null)

Returns the https URL for the Gravatar of the email address specified.
Can optionally pass in the size required as an integer. The size will be contained within a range between 1 - 512 as gravatar will no return sizes greater than 512 of less than 1

```html
<!-- Show image with default dimensions -->
<img src="<?= Gravatar::src('thomaswelton@me.com') ?>">

<!-- Show image at 200px -->
<img src="<?= Gravatar::src('thomaswelton@me.com', 200) ?>">

<!-- Show image at 512px scaled in HTML to 1024px -->
<img src="<?= Gravatar::src('thomaswelton@me.com', 1024) ?>" width=1024>
```

### Gravatar::image($email, $alt = null, $attributes = array())

Returns the HTML for an `<img>` tag

```php
// Show image with default dimensions
echo Gravatar::image('thomaswelton@me.com');

// Show image at 200px
echo Gravatar::image('thomaswelton@me.com', 'Some picture', array('width' => 200, 'height' => 200));

// Show image at 512px scaled in HTML to 1024px
echo Gravatar::image('thomaswelton@me.com', 'Some picture', array('width' => 1024, 'height' => 1024));
```
