# NetBox REST API Filtering Documentation

The __startswith and __icontains (and many others) are part of NetBox's powerful REST API filtering. These are derived from Django's ORM (Object-Relational Mapper) lookups.

Official NetBox Documentation - REST API Filtering:
This is your primary source for understanding what filter lookups are available for each field type.


```
    __ic (contains, case-insensitive)
    __nic (does not contain, case-insensitive)
    __isw (starts with, case-insensitive)
    __nisw (does not start with, case-insensitive)
    __iew (ends with, case-insensitive)
    __niew (does not end with, case-insensitive)
    __ie (exact match, case-insensitive)
    __nie (not exact match, case-insensitive)
```

(Note: __startswith and __contains are case-sensitive versions of __isw and __ic respectively, though the case-insensitive ones are more commonly used for user input.)
You can usually find this by searching "NetBox REST API Filtering" or navigating the official NetBox documentation.