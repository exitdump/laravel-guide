# Route Parameters Validation with Regular Expressions

You can restrict route parameters using **regular expressions** in your route definitions. This helps you validate the format of parameters at the routing level itself.

## Example

```php
// Route with numeric ID only
Route::get('/users/{id}', function ($id) {
    return "User ID: $id";
})->where('id', '[0-9]+');

// Route with alpha username
Route::get('/profile/{username}', function ($username) {
    return "Username: $username";
})->where('username', '[A-Za-z]+');

// Multiple constraints
Route::get('/posts/{year}/{slug}', function ($year, $slug) {
    return "Post from $year: $slug";
})->where([
    'year' => '[0-9]{4}',
    'slug' => '[a-z0-9-]+',
]);
```

## Why It Matters

- Prevents invalid parameters from hitting the controller.

- Improves route clarity and security.

- Reduces need for manual validation inside controllers.
