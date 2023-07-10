# **Basics of TOML**

TOML is short for "Toms Obvious Minimalistic Language", it was introduced in 2013. Now TOML prioritizes humans. It aims to be a minimal configiraton file format that is easy to read that maps un-ambigioulsy and is easy to parse.

Now TOML supports a lot of familar syntax.
1. In TOML we can add `#` to add a comment now that is very convenient, for us Python Devs because thats how we usually write comments.

2. Now we can start with *Key Value* pairs. 
```
# This is an Example of TOML File
name = "My Projects"
version = "0.0.1"
website = "https://example.com"
```

3. Boolian value in TOML in in lower case i.e. `true` & `false`. This is someting that can annoy python devs, but thats good to keep in mind!

4. ALL the Keys in TOML are always interpreted as **STRINGS**!!!

5. Now we are going to create a table, now to create a table we just need to add some square brackets and give it a name. A table is essentially a group any thing that we put inside this will be grouped together.
```
# This is an Example of TOML File
name = "My Projects"
version = "0.0.1"
website = "https://example.com"

[items]
numbers = [1,2,3]
letters = ['a', 'b', 'c']
```
this will be interpreted by python as follows
```
{
    'name': 'My Projects',
    'version': '0.0.1',
    'website': 'https://example.com',
    'iterms': {
        'numbers': [1, 2, 3],
        'letters': ['a', 'b', 'd']
    }
}
```

6. Now we can even create a sub table. `[items.details]`
```
# This is an Example of TOML File
name = "My Projects"
version = "0.0.1"
website = "https://example.com"

[items]
numbers = [1,2,3]
letters = ['a', 'b', 'c']

[items.details]
updated = true
author = "Jon Doe"
```
This will be interprited by python as folows:
```
{
    'name': 'My Projects',
    'version': '0.0.1',
    'website': 'https://example.com',
    'iterms': {
        'numbers': [1, 2, 3],
        'letters': ['a', 'b', 'd'],
        'details': {'updated': True, 'author': 'Jon Doe'}
    }
}
```

7. TOML files do not have a null type!!! Which means, we cannot use `None` and we cannot leave it blank.

8. As for the encoding TOML files use `UTF-8`.

9. Both single and double quotation marks work.

10. We can also create sub keys in the table the syntax is as follows.
```
[database]
file.type = "sqlite"
file.path = "data.db"
```
Now this will be interpreted as follows in python interprter
```
{
    'database': {
            'file': {
                'type': 'sqlite',
                'path': 'data.db'
        }
    }
}
```

11. Creating an in-line table. That is you can directly create a directionay directly. Inline syntax can really clutter your TOML file, so use it in descrition.
```
[inline_table]
inline = {name = "Jhon Doe", age = 30}
```
The output of this function is,
```
{
    'inline_table': {
        'name': 'Jhon Doe',
        'age': 30
    }
}
```

12. Grouped tables are tables that will be grouped together.
```
[[table_group]]
fruit = "Apple"

[[table_group]]
fruit = "Banana"

[[table_group]]
fruit = "Pineapple"
```
The output looks as follows.
The Table group will hold a list of each one of these groups.
```
{
    'table_group': [
        {'fruit': 'Apple'},
        {'fruit': 'Banana'},
        {'fruit': 'Pineapple'}
    ]
}
```
