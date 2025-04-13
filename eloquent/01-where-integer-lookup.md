# Eloquent: Load Data Faster with Integer Lookup

When querying data using a **numeric column** (like `id`, `user_id`, etc.), it’s faster and more efficient to compare against **integers** instead of strings.

---

## Example

```php
// Slower (string comparison)
$user = User::where('id', '42')->first();

// Faster (integer comparison)
$user = User::where('id', 42)->first();
