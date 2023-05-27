# A tutorial on Regular Expressions

Regular expressions are an important tool for web developers to work with text data in a flexible and powerful way. They allow developers to create search patterns that can match complex text patterns with ease. In this tutorial, we will be exploring a specific regular expression 

Let us say that you run an online gaming service. In this, you give special assets to people who buy coupons from you. When one buys a coupon, they have to enter the coupon code in the game. You take this code and validate across your database to see what this coupon code corresponds to. But, there are also people who try to randomly enter digits hoping to get a hit!!
In order to reduce the probability for a random code to hit, you will have to first define a structure for your coupon codes. So, when someone enters a code, you first validate it using your regular expression, if it did not match here, you can directly cancel ther request. This will speed up your database search for all entries on an average.

You have defined your regular expression to be this: (This particular onr is chosen so that you can clearly understand all the possible components of a regex).

```
^(?=.*(\d))[A-Za-z]{3}(?:([\d]){2}){2}\b(?<=(\b\w{4}\b))(?:\w*?|[?&])=(?:(?<=\b\w{2}\b)(\d{3})|([A-Za-z]+\d*))\1\2\3\4$/g
```



## Summary

In this tutorial, we looked at the regular expression and broke it down into its constituent parts to help you grasp the search pattern it defines. We have taken a specific regular expression and showed all it's constituent parts.

The given regular expression matches a coupon code in the format:
  The code must start with at least one digit.
  It is followed by three alphabetic characters exactly.
  There should then be two sets of two consecutive digits.
  There must be a word boundary.
  The current position should be preceded by four word characters.
  Then there can be zero or more word characters, as well as a question mark or an ampersand.
  An equals symbol is required.
  The following portion can be three consecutive numerals followed by two word characters or one or more alphabetic characters followed by a digit.
  The previous sequence of numerals and alphanumeric characters must be repeated in the same order.
  Finally, the code should terminate here.
  
If the format is not present, our regex maching will give us a false result, therefore we can discard the request.

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

## Regex Components

### Anchors
The \^ and \$ characters are called anchors in regular expressions.The \^ character corresponds to the beginning of the line, and the \$ character corresponds to the end of the line. 

for example:
  ```
    '^regular' matches any string starting with 'regular'
    'expression$' matches any string ending with 'expression'.
  ```

```
for ^regular :
  regular expressions
  regularexpression
  regular123
```
```
for expression$ :
  regexpression
  ABC123expression

```

The \^ and \$ anchors in the regular expression ensure that the full string fits the pattern.

### Quantifiers
Quantifiers determine the number of times a character or group should appear. 
Quantifiers include:
```
* matches zero or more times
+ matches one or more times
? matches zero or one time
{n} matches exactly n times
{n,} matches at least n times
{n,m} matches between n and m times
```

some examples:
```
for [a-z]* :
  abcdefg
```
```
for [a-z]{3} :
  abc
```
```
for \d{10} :
  9233443329
```
The quantifiers {3} and {2} in the provided regular expression imply that the preceding [A-Za-z] and \d (digit) characters should be repeated three and two times, respectively.

### OR Operator
In regular expressions, the '|' character is known as the OR operator. It is possible to match multiple patterns separated by the '|' character.

examples:
```
for gym|park :
  would you like to go to the park ?
```
```
for [a-z]|\d :
  3
  b
  c
  8
```

### Character Classes
Character classes correspond to a single character from a group of characters.
they includes:
```
[]: matches any character in the brackets.(For example, [aeiou] will match any vowel).
[^]: matches any character not in the brackets.(For example, [^aeiou] will match any non-vowel).
```

```
for [A-Za-z]* :
  Harrold felt confident that nobody would ever suspect that he is a spy from the United States
  AaBbCcZz
```
```
for [a-z]* :
  harrold felt confident that nobody would ever suspect that he is a spy from the United States
  aabbcczz
```
```
for \d :
  8
```
The \d character class in the regular expression matches any digit from 0 to 9, while the [A-Za-z] character class matches any uppercase or lowercase letter.
### Flags
In regular expressions, flags are used to change the default behaviour of a search pattern. 
Flags include:
```
\g -  matches all occurrences of the pattern.
\i - ignores case when matching.
\m - multi-line flag.
```
examples:
```
for because\g :
  no sentence can end with because because because is a conjunction
```
```
for hello\m :
  hello Sam\nhello Smith 
```
The '\g' flag is used in the following regular expression. This flag enables global matching, which allows a regular expression to find all matches within a string rather than just the first match.

### Grouping and Capturing
In a regular expression, grouping and capturing are employed to build sub-patterns. The '(?:)' non-capturing group is used to group items that do not capture. Whereas, '(' and ')' denote the capturing groups.
They include:
```
(): groups a part of the pattern together
\1: refers to the first captured group
(?:) non-capturing group
```

examples:
```
for (abcdefg) :
  abcdefgabcdefg
```

### Bracket Expressions
Bracket expressions are used to match a single character from a set of characters or from a range of characters.They provide a concise and flexible way to define a group of characters that you want to match.
```
for [&] :
  &
```
```
for [$] :
  $
```
The [?] bracket expression in the given regular expression matches a literal question mark character.
### Greedy and Lazy Match
Greedy matching is a default behaviour in regular expressions that strives to match as many characters as possible. The lazy match attempts to match as few people as possible. 
They are given as:
```
* - greedy, matches as more as possible
*? - lazy, matches as less as possible
```
for example:
```
for b.+l :
  bell
```
```
for b.+?l :
  bel
```
The *? quantifier in the supplied regular expression matches the previous element zero or more times in a lazy (non-greedy) way.

### Boundaries
Boundaries are used to match specified text positions. They provide a way to define specific conditions for matching based on the surrounding context.

```
\b: matches the position between a word character and a non-word character (word boundary)
\B: matches the position between two word characters or two non-word characters (non-worrd boundary)
```
The \b boundary markers are used to denote word boundaries in the specified regular expression.
 

### Back-references
Back-references are used to match a previously captured group. They include bracket refence by number and by name. The number referes to the Nth declared capture group.
They are:
```
\N : back refrences by number
\k : back references by name
```
for example:
```
for (\d+)\s+\1:
  12345 12345
```
```
for (\d+)\s+([a-z]+)\s+\2:
  12345 abcdefg abcdefg
```
Back-references are expressed in the provided regular expression by \1, \2, \3, and \4, which refer to the relevant capturing groups.


### Look-ahead and Look-behind
Look-ahead and look-behind are advanced features in regular expressions. These patterns are used to match patterns that are followed or preceded by a certain pattern but do not include that pattern in the match. 

They are:
```
(?=...) - positive look-ahead
(?<=...) - positive look-behind.
(?!...) - negative look-ahead
(?<!...) - negative look-behind
```

example:
```
for reg(?=ex) :
  regex
  regexpression
```
```
for (?<=[.])[a-z]{3}
  .com
  .org
```
The (?=.*d) positive look-ahead asserts that the string contains at least one digit in the provided regular expression. The (?<=\b\w{4}\b) positive look-behind looks for a word that has exactly four letters before the current place. The (?<=\b\w{2}\b) positive look-behind confirms a term that has exactly two letters before the present place.


## Author
This tutorial was written by Ellie Chayo, a coding bootcamp student. Ellie enjoys exploring different aspects of programming and sharing knowledge with others. You can find more of Ellie's projects and contributions on her [GitHub repository](https://github.com/elliechayo)
