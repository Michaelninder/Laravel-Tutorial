# Laravel Tutorial

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
You can also group routes or apply middleware:
```php
Route::middleware(['auth'])->group(function () {
    Route::get('/dashboard', function () {
        // Only authenticated users may access this route...
    });
});
```
## Views
Views are stored in the `resources/views` directory.
To return a view from a route or controller:
```php
return view('welcome'); // resources/views/welcome.blade.php
```
You can pass data to a view:
```php
return view('profile', ['name' => 'Taylor']);
```
