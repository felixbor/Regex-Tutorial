# Regex Tutorial for email matching and more...


https://gist.github.com/felixbor/f5171ff9eea91cd34e73a83aa870970c
## Summary
Regex (short for "regular expression") is a sequence of characters that define a search pattern. It is a powerful tool used for text processing and search operations.
Regex is used in many programming languages and applications to match, search, and manipulate text based on a specific pattern. It allows you to search for patterns in a string of text, extract specific information from a text file, or validate input from a user.
In this tutorial, we will be covering main components of regular expression using email matching as a example. Moreover, some extra examples will be given and explained. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components:

### Anchors
Anchors have special meaning in regular expressions. They do not match any character. Instead, they match a position before or after characters.
^ – The caret anchor matches the beginning of the text.
$ – The dollar anchor matches the end of the text.

/^([a-z0-9_\.-]+)@([\da-z]+)\.([a-z]{2,5})$/,

 This code in particular is saying that we are looking for something that starts with

^([a-z0-9_\.-]+) 
and ends with:
.([a-z]{2,5})$.
What means the expression in the parentheses will  be covered later in this tutorail,but what the anchor means is that if we are going to find a match and it has follow defined   guidelines.

What implies  tha password must meet   parameters given within the code inside anchors. If it does not, then it is not a match.
### Quantifiers
Quantifiers indicate that the preceding token must be matched a certain number of times.  In other words defines how many times a character, group or class has to be repeated in order to match. By default, quantifiers are greedy, and will match as many characters as possible.

in the given  regex email validator:
/^([a-z0-9_\.-]+)@([\da-z]+)\.([a-z]{2,5})$/

we use quantifier "plus" +  in the first  ([a-z0-9_\.-]+)and second group ([\da-z]+) It refer to the character set [a-z0-9_\.-]  and [\da-z] accordingly. It defines that at least one of characters has to be present in the set to match.

{} to define how many characters shoulld be in the last  group indicated in square brackets,
in our case  it is  from 2 to 5 characters {2,5}

Quantifier "star" * is not used in our example but it's worth mentioning. It means matching 0 or more of the preceding token


### OR Operator
 OR Operator is not used in our validator, but   is important and useful  element of regular expressions 

Or Operator is presented with | element. It Acts like a boolean OR. Matches the expression before or after the |.
It can operate within a group, or on a whole expression.
We  can look at  how it's used in  the following  example  :

/^#?([a-f0-9]{3,6} | [A-F0-9]{3,6})$/
Either first or second set of characters can be used to get a match
[a-f0-9]{6} which will match a 3-6 character long string that contains a combination of a-f letters and 0-9 numbers.

| OR Operator

[A-F0-9]{6}  will match a 3-6 character long string that contains a combination of A-F letters and 0-9 numbers.


### Character Classes
A character class defines a set of characters, any one of which can occur in an input string for a match to succeed.There are a number of predefined character classes and you can also define your own sets.
Set of characters are used in square brackets.

Please see examples of character classes

[a-z] - Matches any lowercase letter from a to z.
[A-Z] - Matches any uppercase letter from A to Z.
[0-9] - Matches any digit from 0 to 9.
[a-zA-Z] - Matches any letter (either uppercase or lowercase) from a to z or A to Z.
[a-zA-Z0-9] - Matches any character that is  a letter or a digit.
[^a-zA-Z0-9] - Matches any character that is not a letter or a digit.
[\d] - Matches any digit (equivalent to [0-9]).
[\s] - Matches any whitespace character (spaces, tabs, newlines).
[\w] - Matches any word character (letters, digits, and underscores).
[^\d] - Matches any character that is not a digit.

 In our email validation code we use :

 [a-z0-9_\.-] any lowercase letter, number, underscore, dot or dash

 [\da-z] any number, lowercase letter

 [a-z] Matches any lowercase letter from a to z.

### Flags

 Flags  are not used in the  email  validation code, so there's no need to describe them  in this tutorial, but we will give just general idea of what flags are.
 Regular xpressions look like following:

 /regex/

 Flags follow the closing forward slash of the expression:

 /regex/i

 /regex/g

 /regex/m

Expression flags change how the expression is interpreted.

i - Makes the whole expression case-insensitive.  For example, /aBc/i would match AbC.

g-  Global search.Retain the index of the last match, allowing subsequent searches to start from the end of the previous match.Without the global flag, subsequent searches will return the same match.

m- When the multiline flag is enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.



### Grouping and Capturing
Grouping and capturing are two powerful features of regular expressions that allow you to match and extract parts of a string.
In our code we use three groups of code which are in parenthasis:
([a-z0-9_\.-]+)
([\da-z]+)
([a-z]{2,5})
Each groupe has to match before  moving to the next one.


### Bracket Expressions
Bracket expressions [] are meant to match any character in the square brackets. 
it's  used with  character classes

### Greedy and Lazy Match
In regular expressions, greedy and lazy matching are two ways to control how much text is matched by a quantifier, which is a special character that specifies how many times a previous character or group should be matched

Here are some examples of greedy and lazy quantifiers:

a+ matches one or more "a" characters, as many as possible (greedy).

a+? matches one or more "a" characters, as few as possible (lazy).

a* matches zero or more "a" characters, as many as possible (greedy).

a*? matches zero or more "a" characters, as few as possible (lazy).

a? matches zero or one "a" character, as many as possible (greedy).

a?? matches zero or one "a" character, as few as possible (lazy).

### Boundaries
In regular expressions, boundaries are special characters that allow you to match patterns that occur at specific positions within a string. Boundaries are useful for creating patterns that match entire words, sentences, or lines, as well as for ensuring that a match does not occur within a certain context.
Here are some common boundary characters in regular expressions:

^ matches the beginning of a string or line.

$ matches the end of a string or line.

 \b matches a word boundary, which is a zero-width position between a word character (as defined by \w) and a non-word 
character (as defined by \W).

 \B matches a non-word boundary, which is a zero-width position that is not at a word boundary.


### Back-references

Backreferences are a feature of regular expressions that allow you to refer to a previously matched group in your pattern. A group is a sub-expression enclosed in parentheses, which captures the matched text so that it can be used later in the regular expression or in the replacement text of a search-and-replace operation.
Back-references are specified with backslash and a single digit (e.g. ‘\1’).
To use a backreference, you simply refer to the numbered group that you want to match again. For example, if you have a regular expression that matches a phone number and captures the area code in a group, you could use a backreference to match the same area code again later in the pattern. Here's an example:
(\d{3})-\d{3}-\d{4}
In this regular expression, the first group captures a three-digit area code, and the rest of the pattern matches a hyphen, three digits, another hyphen, and four digits. To use a backreference to match the same area code again later in the pattern, you would use the backslash followed by the group number, like this:
(\d{3})-\d{3}-\d{4}\s+\1
In this modified regular expression, the \1 backreference matches the same three-digit area code that was captured by the first group. The \s+ matches one or more whitespace characters, so this pattern would match a phone number followed by one or more spaces and the same area code again

### Look-ahead and Look-behind
Even though  not being used in our email validator,Look-ahead and Look-behind have to be covered in our tutorial.

Look-ahead and Look-behind can be positive and negative. 

Positive look-ahead (?=ABC) matches a group after the main expression without including it in the result.

Negative look-ahead  (?!ABC)specifies a group that can not match after the main expression (if it matches, the result is discarded).

Positive Look-behind  (?<=ABC) matches a group before the main expression without including it in the result.

Negative Look-behind  (?<!ABC) Specifies a group that can not match before the main expression (if it matches, the result is discarded).

## Author