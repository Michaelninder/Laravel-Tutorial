# Laravel Tutorial

---
## Routes
In Laravel, all routes are defined in the `routes/web.php` file for web interfaces or `routes/api.php` for API routes.
## Router Methods
```php
Route::get($uri, $callback);
Route::post($uri, $callback);
Route::put($uri, $callback);
Route::patch($uri, $callback);
Route::delete($uri, $callback);
Route::options($uri, $callback);
Route::view($uri, $view, $data = []);
Route::redirect($from, $to, $status = 302);
```
uri: `'/'` or  `'/some/route'`

callback: `function () { // ... }` or `[Controller::class, 'myfunction']`

---
You can also group routes or apply middleware:
```php
Route::middleware(['auth'])->group(function () {
    Route::get('/dashboard', function () {
        // Only authenticated users may access this route...
    });
});
```
---

## Views
Create a controller using Artisan:
```
php artisan make:view auth.login // creates resources/views/auth/login.blade.php
```
Views are stored in the `resources/views` directory.
To return a view from a route or controller:
```php
return view('welcome'); // resources/views/welcome.blade.php

return view('auth.login'); // resources/views/auth/login.blade.php
```
---
### Passing Data to Views
You can pass data to a view in several ways:
```php
return view('profile', ['name' => 'Michaelninder']); // fixed value

return view('profile', ['name' => $name]); // varible

return view('profile', compact('name')); // if both values (varible and datavalue have the same name
```
Example Blade File (resources/views/profile.blade.php)
```php
<h1>Hello, {{ $name }}</h1>
```
Blade is Laravel’s templating engine. You can use directives like:
```php
@if ($user)
    Hello, {{ $user->name }}
@endif
```
This section will soon be continued with loops, conditionals, layouts (`@extends`, `@section`, `@yield`) and componentsa

---
## Controllers
Create a controller using Artisan:
```
php artisan make:controller AuthController
```
Basic example:
```php
class AuthController extends Controller
{
     public function showLogin()
    {
        return view('auth.login');
    }
}
```
Define route to controller:
```php
Route::get('/login', [AuthController::class, 'showLogin']);
```
