# Regex

All regex expressions made on diferent languages


## Python 3:

### Detect Floating Point Number:
    r'^[+-]?\d*\.\d+$'
    
### Valid Roman Numerals:
    r'M{0,3}(C[MD]|D?C{0,3})(X[CL]|L?X{0,3})(I[VX]|V?I{0,3})$'

### Valid phone number:
    On this example, it must start with 7,8 or 9 and be length 9
    r'^[789]\d{8}$'

### Valid Email Address:
    The username starts with an English alphabetical character, and any subsequent characters
    consist of one or more of the following: alphanumeric characters, -,., and _.
    The domain and extension contain only English alphabetical characters.
    The extension is max length 3, min length 1.
    
    r'^[a-zA-Z][a-zA-Z1-9._-]* <[a-z][a-z1-9._-]*@[a-z]+\.[a-z]{1,3}>$'

### Valid Hex Color Code
    r'(?!^)(#[a-fA-F0-9]{6}|#[a-fA-F0-9]{3})'





## Java:

### Valid IP address:
    "^((([0-1]?[0-9]?[0-9])|([0-2]?[0-4]?[0-9])|([2]?[0-5]?[0-5]))[.]){3}(([0-1]?[0-9]?[0-9])|([0-2]?[0-4]?[0-9])|([2]?[0-5]?[0-5]))"
    
### Duplicated word on text:
    "\\b(\\w+)(?:\\W+\\1\\b)+"
    
### Valid user name:

    The username consists of 8 to 30 characters inclusive. If the username
    consists of less than 8 or greater than 30 characters, then it is an 
    invalid username.
    The username can only contain alphanumeric characters and underscores (_).
    Alphanumeric characters describe the character set consisting of lowercase
    characters [a-z], uppercase characters [A-Z], and digits [0-9].
    The first character of the username must be an alphabetic character.
    
    "[a-zA-Z][a-zA-Z_0-9]{7,29}"
