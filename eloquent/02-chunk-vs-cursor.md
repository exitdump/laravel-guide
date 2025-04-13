# Eloquent: Chunk vs Cursor

When working with large datasets in Laravel, `chunk()` and `cursor()` help you avoid memory issues by not loading everything into memory at once. But they work differently and are suited for different tasks.

---

## `chunk()`

- Breaks records into **batches** (chunks)
- **Each chunk loads a fresh query**
- Ideal for **bulk processing**

```php
User::chunk(100, function ($users) {
    foreach ($users as $user) {
        // Process user
    }
});
```



## Key Differences

| Feature             | `chunk()`                               | `cursor()`                          |
|---------------------|------------------------------------------|-------------------------------------|
| Memory Usage        | Medium (loads a chunk of records)        | Very Low (one record at a time)     |
| Query Count         | Multiple (one per chunk)                 | Single                              |
| Speed               | Faster for batch processing              | Slower (fetches record by record)   |
| Best Use Case       | Bulk updates/deletes                     | Streaming large datasets            |
| Lazy Loading        | No                                       | Yes                                 |
| Pagination Support  | Yes (via chunk size)                     | No (sequential only)                |
