# Regular Expressions


## Basic Syntax

- `/.../`: Start and end regex delimiters
- `|`: Alternation
- `()`: Grouping


## Position Matching

- `^`: Start of string or start of line in multi-line mode
- `\A`: Start of string
- `$`: End of string or end of line in multi-line mode
- `\Z`: End of string
- `\b`: Word boundary
- `\B`: Not word boundary
- `\<`: Start of word
- `\>`: End of word


## Character Classes

- `\s`: Whitespace
- `\S`: Not whitespace
- `\w`: Word
- `\W`: Not word
- `\d`: Digit
- `\D`: Not digit
- `\x`: Hexade­cimal digit
- `\O`: Octal digit


## Special Characters

- `\n`: Newline
- `\r`: Carriage return
- `\t`: Tab
- `\v`: Vertical tab
- `\f`: Form feed
- `\xxx`: Octal character xxx
- `\xhh`: Hex character hh


## Groups and Ranges

- `.`: Any character except newline (\n)
- `(a|b)`: a or b
- `(…)`: Group
- `(?:…)`: Passive (non-c­apt­uring) group
- `[abc]`: a, b or c
- `[^abc]`: Not a, b or c
- `[a-z]`: Letters from a to z
- `[A-Z]`: Uppercase letters from A to Z
- `[0-9]`: Digits from 0 to 9

> Note: Ranges are inclusive.


## Quantifiers

- `*`: 0 or more
- `+`: 1 or more
- `?`: 0 or 1
- `{3`: Exactly 3
- `{3,}`: 3 or more
- `{3,5}`: 3, 4 or 5

> Note: Quantifiers are greedy - they match as many times as possible. Add a ? after the quantifier to make it ungreedy.


## Escape Sequences

- `\`:Escape following character. Used to escape any of the following metacharacters: {}[]()^$.|*+?\.
- `\Q`: Begin literal sequence
- `\E`: End literal sequence


## String Replacement

- `$1`: 1st group
- `$2`: 2nd group
- `$n`: nth group
- `$``: Before matched string
- `$'`: After matched string
- `$+`: Last matched string
- `$&`: Entire matched string

> Note: Some regex implem­ent­ations use \ instead of $.


## Assertions

- `?=`: Lookahead assertion
- `?!`: Negative lookahead
- `?<=`: Lookbehind assertion
- ``?!=, ?<!``: Negative lookbehind
- `?>`: Once-only subexp­ression
- `?()`: Condition if-then
- `?()|`: Condition if-then-else
- `?#`: Comment


## POSIX

- `[:upper:]`: Uppercase letters
- `[:lower:]`: Lowercase letters
- `[:alpha:]`: All letters
- `[:alnum:]`: Digits and letters
- `[:digit:]`: Digits
- `[:xdigit:]`: Hexade­cimal digits
- `[:punct:]`: Punctu­ation
- `[:blank:]`: Space and tab
- `[:space:]`: Blank characters
- `[:cntrl:]`: Control characters
- `[:graph:]`: Printed characters
- `[:print:]`: Printed characters and spaces
- `[:word:]`: Digits, letters and underscore


## Pattern Modifiers

- `g`: Global match
- `i`: Case-i­nse­nsitive
- `m`: Multi-line mode. Causes ^ and $ to also match the start/end of lines.
- `s`: Single-line mode. Causes . to match all, including line breaks.
- `x`: Allow comments and whitespace in pattern
- `e`: Evaluate replac­ement
- `U`: Ungreedy mode

## Example

   #### RegExp.exec(string)
   - Applies the RegExp to the given string, and returns the match information.
     
     `var regex = '/s(amp)le/i';`  
     `var match = regex.exec("Sample text");`  
     `match then contains ["Sample","amp"]`
     
   #### RegExp.test(string)
   - Tests if the given string matches the Regexp, and returns true if matching, false if not.
     
     `var regex = '/sample/';`  
     `var match = regex.test("Sample text");`  
     `match then contains false`
     
   #### String.match(pattern)
   - Matches given string with the RegExp. With g flag returns an array containing the matches, without g flag returns just the
     first match or if no match is found returns null.
   
     `var str1 = 'Watch out for the rock!';`  
     `var str = str1.match(/r?or?/g);`  
     `str then contains ["o","or","ro"]`  
     
   #### String.search(pattern)
   - Matches RegExp with string and returns the index of the beginning of the match if found, -1 if not.
     
     `var str = 'Watch out for the rock!';`   
     `var index = str.search(/for/);`  
     `index then contains 10`
     
   #### String.replace(pattern,string)
   - Replaces matches with the given string, and returns the edited string.
   
     `var str = 'Liorean said: My name is Liorean!';`  
     `var replacedStr = str.replace(/Liorean/g,'Big Fat Dork');`  
     `replacedStr then contains "Big Fat Dork said: My name is Big Fat Dork!"`
     
   #### String.split(pattern)
   - Cuts a string into an array, making cuts at matches.
     
     `var str1 = 'I am confused';`  
     `var str = str1.split(/\s/g);`  
     `str then contains ["I","am","confused"]`
     
     
## Common Used Regex
  
  #### Decimal Input
  
   - Positive Integers `/^\d+$/`
   - Negative Integers `/^-\d+$/`
   - Integer `/^-?\d+$/`
   - Positive Number `^/\d*\.?\d+$/`
   - Negative Number  `/^-\d*\.?\d+$/`
   - Positive Number or Negative Number `/^-?\d*\.?\d+$/`
   - Phone number `/^\+?[\d\s]{3,}$/`
   - Phone with code  `/^\+?[\d\s]+\(?[\d\s]{10,}$/`
   - Year 1900-2099  `/^(19|20)\d{2}$/`
   - Date (dd mm yyyy, d/m/yyyy, etc.) `/^([1-9]|0[1-9]|[12][0-9]|3[01])\D([1-9]|0[1-9]|1[012])\D(19[0-9][0-9]|20[0-9][0-9])$/`
   
  #### Alphabetic Input
  
   - Personal Name `/^[\w.']{2,}(\s[\w.']{2,})+$/`
   - Username `/^[\w\d_.]{4,}$/`
   - Password at `/^.{6,}$/` or `/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{6,12}$/`
   - Password or empty input  `/^.{6,}$|^$/`
   - email `/^[_]*([a-z0-9]+(\.|_*)?)+@([a-z][a-z0-9-]+(\.|-*\.))+[a-z]{2,6}$/` or `/^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/`
   - domain `/^([a-z][a-z0-9-]+(\.|-*\.))+[a-z]{2,6}$/`
   - URL `/^(?:(?:https?|ftp):\/\/)(?:\S+(?::\S*)?@)?(?:(?!10(?:\.\d{1,3}){3})(?!127(?:\.\d{1,3}){3})(?!169\.254(?:\.\d{1,3}){2}) (?!192\.168(?:\.\d{1,3}){2})(?!172\.(?:1[6-9]|2\d|3[0-1])(?:\.\d{1,3}){2})(?:[1-9]\d?|1\d\d|2[01]\d|22[0-3])(?:\.(?:1?\d{1,2}|2[0-4]\d|25[0-5])){2}(?:\.(?:[1-9]\d?|1\d\d|2[0-4]\d|25[0-4]))|(?:(?:[a-z\u00a1-\uffff0-9]+-?)*[a-z\u00a1-\uffff0-9]+)(?:\.(?:[a-z\u00a1-\uffff0-9]+-?)*[a-z\u00a1-\uffff0-9]+)*(?:\.(?:[a-z\u00a1-\uffff]{2,})))(?::\d{2,5})?(?:\/[^\s]*)?$/i` or `/^(http|https|ftp):[\/]{2}([a-zA-Z0-9\-\.]+\.[a-zA-Z]{2,4})(:[0-9]+)?\/?([a-zA-Z0-9\-\._\?\,\'\/\\\+&amp;%\$#\=~]*)/`
   
  #### Other
  
   - Match no input `/^$/` 
   - Match blank input `/^\s\t*$/`
   - Match New line `/[\r\n]|$/`
   - Match white Space `/^\s+$/`
   - Match HTML Tags `/<([\w]+).*>(.*?)<\/\1>/`
   
   #### Explanation of some of the above regex:
   
   `Matching a password: ^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{6,12}$`
   - `6 to 12 characters in length`  
   `Must have at least one uppercase letter`  
   `Must have at least one lower case letter`  
   `Must have at least one digit`  
   `Should contain other characters`
      
      Let’s explain each pattern of the above expression:
      
      * ^ asserts position at start of the string
      * (?=.*[a-z]) positive lookahead, asserts that the regex .*[a-z] can be matched:
        - .* matches any character (except newline) between zero and unlimited times
        - [a-z] matches a single character in the range between a and z (case sensitive)
      * (?=.*[A-Z]) positive lookahead, asserts that the regex .*[A-Z] can be matched:
        - .* matches any character (except newline) between zero and unlimited times
        - [A-Z] matches a single character between A and Z (case sensitive)
      * (?=.*\d) positive lookahead, asserts that the regex *\dcan be matched:
        - .* matches any character (except newline) between zero and unlimited times
        - \d matches a digit [0-9]
      * .{6,12} matches any character (except newline) between 6 and 12 times
      * $ asserts position at end of the string
      
   `Matching URL: ^(http|https|ftp):[\/]{2}([a-zA-Z0-9\-\.]+\.[a-zA-Z]{2,4})(:[0-9]+)?\/?([a-zA-Z0-9\-\._\?\,\'\/\\\+&amp;%\$#\=~]*)`
   - `Must start with http or https or ftp followed by ://`  
   `Must match a valid domain name`  
   `Could contain a port specification (http://www.localhost:8080)`  
   `Could contain digit, letter, dots, hyphens, forward slashes, multiple times`
      
      Let’s explain each pattern of the above expression:
      
      * ^ asserts position at start of the string
      * capturing group (http|https|ftp), captures http or https or ftp
      * : escaped character, matches the character : literally
      * [\/]{2} matches exactly 2 times the escaped character /
      * capturing group ([a-zA-Z0-9\-\.]+\.[a-zA-Z]{2,4}):
        - [a-zA-Z0-9\-\.]+ matches one and unlimited times character in the range between a and z, A and Z, 0 and 9, the character - literally and the character . literally
        - \. matches the character . literally
        - [a-zA-Z]{2,4} matches a single character between 2 and 4 times between a and z or A and Z (case sensitive)
      * capturing group (:[0-9]+)?:
        - quantifier ? matches the group between zero or more times
        - : matches the character : literally
        - [0-9]+ matches a single character between 0 and 9 one or more times
      * \/? matches the character / literally zero or one time
      * capturing group ([a-zA-Z0-9\-\._\?\,\'\/\\\+&amp;%\$#\=~]*):
        - [a-zA-Z0-9\-\._\?\,\'\/\\\+&amp;%\$#\=~]* matches between zero and unlimited times a single character in the range a-z, A-Z, 0-9, the characters: -._?,'/\+&amp;%$#=~.
