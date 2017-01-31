# Laravel 5.x Scaffold Generator

[![Packagist](https://img.shields.io/packagist/dt/summerblue/generator.svg?style=flat-square)](https://packagist.org/packages/laralib/l5scaffold)
[![Tag](https://img.shields.io/github/tag/summerblue/generator.svg)](https://github.com/laralib/l5scaffold/tags)

Laravel Scaffold Generator, for Laravel 5.3.

## Install

### Step 1: Install Through Composer

```
composer require 'summerblue/generator' --dev
```

### Step 2: Add the Service Provider

Open `/app/Providers/AppServiceProvider.php` and, to your **register** function, add:

```
public function register()
{
     if (app()->environment() == 'local' || app()->environment() == 'testing') {

        $this->app->register(\Summerblue\Generator\GeneratorsServiceProvider::class);

    }
}
```

### Step 3: Run Artisan!

You're all set. Run `php artisan` from the console, and you'll see the new commands `make:scaffold`.

## Examples

Use this command to generator scaffolding of **Project** in your project:

> php artisan make:scaffold Projects --schema="name:string:index,description:text:nullable,subscriber_count:integer:unsigned,default(0)"

This command will generate:

```
$ php artisan make:scaffold Projects --schema="name:string:index,description:text:nullable,subscriber_count:integer:unsigned,default(0)"

----------- scaffolding: Project -----------

+ ./database/migrations/2017_01_30_233548_create_projects_table.php
+ ./database/factories/ModelFactory.php
+ ./database/seeds/ProjectTableSeeder.php
+ ./database/seeds/DatabaseSeeder.php (Updated)
+ ./app/Models/Model.php (Updated)
+ ./app/Models/Traits/ProjectOperation.php
+ ./app/Models/Project.php
+ ./app/Http/Controllers/ProjectController.php
+ ./app/Http/Requests/Request.php
+ ./app/Http/Requests/ProjectStoreRequest.php
+ ./app/Http/Requests/ProjectUpdateRequest.php
+ ./app/Policies/Policy.php
+ ./app/Policies/ProjectPolicy.php
+ ./app/Providers/AuthServiceProvider.php (Updated)
+ ./routes/web.php (Updated)

--- Views ---
   + create_and_edit.blade.php
   + index.blade.php
   + show.blade.php
+ ./resources/views/error.blade.php
Migrated: 2017_01_30_233548_create_projects_table

----------- -------------------- -----------
-----------   >DUMP AUTOLOAD<    -----------
```

## Explain

Generate the following:

- Migration
- Seed, add ModelFactory entry, and DatabaseSeeder entry
- Base Model class, Model and helper trait
- Resource Controller
- Base FormRequest class and StoreRequest, UpdateRequest
- Policy and Policy base class, auto register AuthServiceProvider class
- Update routes file to register resource route
- Add error page view
- Create and Edit action share the same view

## Future Plan

- API
- Admin
- Auto fill FormRequest rule
- Auto fill ModelFactory filed

## Thinks to
- [laralib/l5scaffold](https://github.com/laralib/l5scaffold)