# Regex

All regex expressions made on diferent languages

## Java:

### Valid IP address:
    "^((([0-1]?[0-9]?[0-9])|([0-2]?[0-4]?[0-9])|([2]?[0-5]?[0-5]))[.]){3}(([0-1]?[0-9]?[0-9])|([0-2]?[0-4]?[0-9])|([2]?[0-5]?[0-5]))"
    
### Duplicated word on text:
    "\\b(\\w+)(?:\\W+\\1\\b)+"
    
### Valid user name:
    The username consists of 8 to 30 characters inclusive. If the username consists of less than 8 or greater than 30 characters, then it is an invalid username.
    The username can only contain alphanumeric characters and underscores (_). Alphanumeric characters describe the character set consisting of lowercase characters [a-z], uppercase characters [A-Z], and digits [0-9].
    The first character of the username must be an alphabetic character.
    
    "[a-zA-Z][a-zA-Z_0-9]{7,29}
