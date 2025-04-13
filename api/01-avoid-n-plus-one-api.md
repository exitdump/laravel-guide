# Avoid N+1 Queries in API Resources

You can avoid **N+1 queries** in API Resources by using the `whenLoaded()` method. This ensures that related models (like `department`) are only accessed if they have already been eager-loaded.

## Problem

Without `whenLoaded()`, calling a relationship inside a Resource will trigger a **separate query** for every item, causing an N+1 issue.

## Example

```php
// EmployeeResource
class EmployeeResource extends JsonResource
{
    public function toArray($request): array
    {
        return [
            'id' => $this->uuid,
            'fullName' => $this->full_name,
            'email' => $this->email,
            'jobTitle' => $this->job_title,
            'department' => DepartmentResource::make(
                $this->whenLoaded('department')
            ),
        ];
    }
}
```

### Why It Matters
- whenLoaded() prevents unnecessary queries if the relationship wasn’t eager loaded.

- Ensures that your API stays fast and efficient.

- Without it, Laravel will lazy-load the relationship, causing one query per resource.
