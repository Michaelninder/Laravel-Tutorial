# Laravel Tutorial
<br>
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
