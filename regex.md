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
     
     var regex = '/s(amp)le/i';
     var match = regex.exec("Sample text");
     match then contains ["Sample","amp"]
     
   #### RegExp.test(string)
   - Tests if the given string matches the Regexp, and returns true if matching, false if not.
     
     var regex = '/sample/';
     var match = regex.test("Sample text");
     match then contains false
     
   #### String.match(pattern)
   - Matches given string with the RegExp. With g flag returns an array containing the matches, without g flag returns just the
     first match or if no match is found returns null.
   
     var str1 = 'Watch out for the rock!';
     var str = str1.match(/r?or?/g);
     str then contains ["o","or","ro"]
     
   #### String.search(pattern)
   - Matches RegExp with string and returns the index of the beginning of the match if found, -1 if not.
     
     var str = 'Watch out for the rock!'; 
     var index = str.search(/for/);
     index then contains 10
     
   #### String.replace(pattern,string)
   - Replaces matches with the given string, and returns the edited string.
   
     var str = 'Liorean said: My name is Liorean!'
     var replacedStr = str.replace(/Liorean/g,'Big Fat Dork')
     replacedStr then contains "Big Fat Dork said: My name is Big Fat Dork!"
     
   #### String.split(pattern)
   - Cuts a string into an array, making cuts at matches.
     
     var str1 = 'I am confused';
     var str = str1.split(/\s/g);
     str then contains ["I","am","confused"]
