---
title: Branding
description: Customize the look to match your brand
extends: _layouts.documentation
section: main
---

There are times when you want the visual style of the platform to match your brand.
After installation, two settings are provided that are located in `config/platform.php`:

```php
'template' => [
    'header' => null,
    'footer' => null,
],
```

To change the page header or footer, you must specify your own `blade` templates.


## Change logo and name

Create a new directory inside the `/resources/views` folder of your project, name it  `brand`, create a new blade file inside, and name it header.blade.php.
Then the full path will look like: `/resources/views/brand/header.blade.php`.


```php
resources          
└── views
    └── brand
        └── header.blade.php
```

 
Suppose that we are creating a system for a fictitious analytical agency, we will make changes to the file just created:

```php
//resources/views/brand/header.blade.php.cd ..

@push('head')
    <link
        href="/favicon.ico"
        id="favicon"
        rel="icon"
    >
@endpush

<p class="h2 n-m font-thin v-center">
    <x-orchid-icon path="database"/>

    <span class="m-l d-none d-sm-block">
        Analytics
        <small class="v-top opacity">Nest</small>
    </span>
</p>
```
 
In order for the created template to be used instead of the standard one, you must specify it in the configuration file,
just as if passing an argument in the `view('brand.header')` helper:

  
```php
//`config/platform.php`

'template' => [
    'header' => 'brand.header',
    'footer' => null,
],
```

> **Note.** The configuration file may be cached, and the changes will not take effect until the `php artisan config:clear` command is executed


In the same way, we can change the bottom of the page, again create a new file `/resources/views/brand/footer.blade.php` with the following contents:


```php
<p class="small m-n">
    © Copyright {{date('Y')}} <a href="//example.com" target="_blank">"Analytics Nest"</a>
</p>
```

Also making changes to the configuration file:

```php
//`config/platform.php`

'template' => [
    'header' => 'brand.header',
    'footer' => 'brand.footer',
],
```

