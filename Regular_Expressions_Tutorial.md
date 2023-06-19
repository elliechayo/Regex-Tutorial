# Regular Expressions Tutorial

Regex, short for regular expression, is a sequence of characters that defines a search pattern. It is a powerful tool used for pattern matching and manipulating strings of text. Regular expressions are supported by various programming languages and text editors, providing a standardized syntax for expressing complex search patterns.

Some common use cases of regular expressions include: String matching, Validation, Data extraction, Text manipulation. In this tutorial, we will be exploring a regular expressions that matches an email.

```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

## Summary

In this regex tutorial, we explore the commonly used email matching regex pattern: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`. The pattern is divided into three main components: the username, the domain, and the top-level domain (TLD).

The username component, `[a-z0-9_\.-]+`, matches one or more lowercase letters, digits, underscores, dots, or hyphens.

The domain component, `[\da-z\.-]+`, matches one or more lowercase letters, digits, dots, or hyphens.

The TLD component, `[a-z\.]{2,6}`, matches between 2 and 6 lowercase letters or dots.

By combining these components and utilizing anchors (^ and $) to mark the start and end of the string, this regex pattern can be used to validate and match email addresses.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

An anchor is a metacharacter used to assert a position in the string being matched. Anchors do not match any characters themselves; they only represent a position in the string. Anchors are useful for specifying where a pattern should occur relative to the beginning or end of the string or relative to other characters.

- `^` - Matches the start of the string.
- `$` - Matches the end of the string.

Example:

```
^([a-z]+)$ would match a string consisting of lowercase letters from start to end.
```

### Quantifiers

Quantifiers are special characters that specify the number of occurrences of a preceding element or group in the pattern. They allow you to match patterns with different quantities of characters or groups.

- `+` - Matches one or more occurrences of the preceding element.
- `*` - Matches zero or more occurrences of the preceding element.
- `?` - Matches zero or one occurrences of the preceding element.
- `{n}` - Matches exactly n times
- `{n, }` - Matches at least n times
- `{n, m}` - Matches between n and m occurrences of the preceding element.

Example:

```
In the regex ([0-9]{2,4}), it matches 2 to 4 consecutive digits.
```

### Character Classes

Character classes are a way to specify a set of characters that can be matched at a particular position in a string. They allow you to define a range or a group of characters that you want to match. Character classes are enclosed in square brackets [] within a regex pattern.

- []: matches any character in the brackets.
- [^]: matches any character that are not in the brackets

Example:

```
[a-z0-9_\.-]: Matches a lowercase letter, digit, underscore, dot, or hyphen.
[\da-z\.-]: Matches a digit, lowercase letter, dot, or hyphen.
[a-z\.]: Matches a lowercase letter or dot.
```

### Flags

Flags are optional parameters that modify the behavior of the regex pattern matching. Flags are usually added after the closing delimiter of the regex pattern and are denoted by a letter or combination of letters.
Flags include:

```
\g -  matches all occurrences of the pattern.
\i - ignores case when matching.
\m - multi-line flag.
```

Example:

```
the pattern "/\d/g" will match all occurrences of digits in the input string.
```

The '\g' flag is used in the following regular expression. This flag enables global matching, which allows a regular expression to find all matches within a string rather than just the first match.

### Grouping and Capturing

In a regular expression, grouping and capturing are employed to build sub-patterns. The '(?:)' non-capturing group is used to group items that do not capture. Whereas, '(' and ')' denote the capturing groups.

They include:

- (): groups a part of the pattern together
- \1: refers to the first captured group
- (?:) non-capturing group

Example:

```
([a-z0-9_\.-]+): Captures a group of lowercase letters, digits, underscores, dots, or hyphens.
([\da-z\.-]+): Captures a group of digits, lowercase letters, dots, or hyphens.
([a-z\.]{2,6}): Captures a group of lowercase letters or dots, between 2 and 6 characters long.
```

### Bracket Expressions

Bracket expressions are used to match a single character from a set of characters or from a range of characters. They provide a concise and flexible way to define a group of characters that you want to match.

Example:

```
[a-z0-9_\.-]: Matches any character within the range of lowercase letters, digits, underscore, dot, or hyphen.
[\da-z\.-]: Matches any character within the range of digits, lowercase letters, dot, or hyphen.
In the regex ^[a-z]+[\d-]+[A-Z]$, it matches a string that starts with lowercase letters, followed by digits or hyphens, and ends with an uppercase letter.
```

### Greedy and Lazy Match

Greedy matching is the default behavior of quantifiers and it tries to match as much text as possible while still allowing the overall pattern to match.

```
Example: `a.*b` applied to the string "aabab"
The greedy match would result in a single match that captures the entire substring "aabab" because `.*` matches as many character as possible.
```

Lazy matching, also known as non-greedy or minimal matching, matches as little text as possible and it can be achieved by appending a `?` after the quantifier.

```
Example: `a.*?b` applied on the string "aabab"
This would result in two matches, the first match would capture "aab" and then the second match would capture "ab".
```

## Author
 Written by Ellie Chayo, a web development student.  You can find more of Ellie's projects and contributions on her [GitHub repository](https://github.com/elliechayo)






