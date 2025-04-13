# Validation: Custom Error Messages

By default, Laravel provides standard error messages for validation. But you can easily customize them to make them more user-friendly.

## Example

```php
$request->validate([
    'email' => 'required|email',
    'password' => 'required|min:8',
], [
    'email.required' => 'We need your email address!',
    'password.min' => 'Your password must be at least 8 characters long.',
]);
```

---



#### Or : Create a Custom Request

Generate a custom request using the Artisan command:

```bash
php artisan make:request CustomUserRequest
```

```php
namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class CustomUserRequest extends FormRequest
{
    public function authorize()
    {
        // Return true if the user is authorized to make this request
        return true;
    }

    public function rules()
    {
        return [
            'email' => 'required|email',
            'password' => 'required|min:8',
        ];
    }

    public function messages()
    {
        return [
            'email.required' => 'Please provide your email address.',
            'email.email' => 'Please enter a valid email address.',
            'password.required' => 'A password is required.',
            'password.min' => 'Your password must be at least 8 characters long.',
        ];
    }
}


