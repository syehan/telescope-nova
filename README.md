# Laravel Telescope for Nova

An extension Laravel Lifecycle embedding Telescope to Nova Admin Panel.

<p style="text-align: center;" align="center">

</p>

## Requirements
- PHP 8.0 or higher
- Nova 4

## Installation

You can install the package via composer:

```bash
composer require syehan/telescope-nova
```

## Usage

To use this tools just registering in NovaServiceProvider.php like this :

```php
<?php

namespace App\Providers;

use Laravel\Nova\{Nova, NovaApplicationServiceProvider, Menu};
use Syehan\TelescopeNova\TelescopeNova;

class NovaServiceProvider extends NovaApplicationServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        parent::boot();
    }
    
    /**
     * Get the tools that should be listed in the Nova sidebar.
     *
     * @return array
     */
    public function tools()
    {
        return [
            new TelescopeNova // <- JUST ADD LIKE THIS
         ];
    }
}
```
