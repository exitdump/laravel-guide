
# Model: Using Scopes to Encapsulate Query Logic

Scopes allow you to define common query constraints as methods on your model, making it reusable and clean.

## Example

```php
// In the User model
public function scopeActive($query)
{
    return $query->where('status', 'active');
}

// Using the scope
$activeUsers = User::active()->get();
```


### Why It Matters
Keeps your queries DRY (Don’t Repeat Yourself).

Encapsulates complex query logic into reusable methods.
