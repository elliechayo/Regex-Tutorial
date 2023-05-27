## Tutorial: Matching an Email with Regular Expressions

### Introduction

Understanding regular expressions (regex) is essential, especially when it comes to validating and matching email addresses.  Email validation is a crucial task in web development to ensure that user-provided email addresses are correctly formatted. Regular expressions provide a powerful tool for matching and validating email addresses. In this tutorial, we will explore how to use regular expressions to match email addresses and ensure their validity.

By the end of this tutorial, you will have a solid understanding of the regex components used to match email addresses, allowing you to implement email validation in your web applications.

### Summary
In this tutorial, we will explore a regular expression pattern that can match and validate email addresses. The regex pattern is as follows:

```
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

Let's break down this pattern, understand the purpose and functionality of each part of the regex and how it contributes to matching and validating email addresses.



## Table of Contents

- [Start and End Anchors](#start-and-end-anchors)
- [Local Part: Matching Username](#local-part-matching-username)
- [The At Symbol: Separating Username and Domain](#the-at-symbol-separating-username-and-domain)
- [Domain Part: Matching Domain Name](#domain-part-matching-domain-name)
- [Top-Level Domain: Matching TLD](#top-level-domain-matching-tld)
- [Usage in JavaScript](#usage-in-javascript)


## Start and End Anchors
The ^ and $ symbols in the regex pattern represent the start and end of the string, respectively. They ensure that the entire email matches the pattern and doesn't contain any extra characters before or after.

## Local Part: Matching Username
The local part of an email refers to the username before the at symbol (@). We use [a-zA-Z0-9._%+-]+ to match one or more characters that can be letters (both uppercase and lowercase), digits, or special characters often allowed in email addresses, such as dots, underscores, percent signs, plus signs, or hyphens.

## The At Symbol: Separating Username and Domain
The @ symbol is a literal character that separates the local part from the domain part in an email address. It must be present in a valid email address for a match to occur.

## Domain Part: Matching Domain Name
The domain part of an email follows the at symbol (@). We use [a-zA-Z0-9.-]+ to match one or more characters that can be letters, digits, dots, or hyphens in the domain name.

## Top-Level Domain: Matching TLD
The top-level domain (TLD) represents the domain extension, such as .com, .org, or .edu. We use [a-zA-Z]{2,} to match two or more letters in the TLD.

## Usage in JavaScript

To validate an email address using this regular expression pattern in JavaScript, follow these steps:

1. Define the regular expression pattern:
```
const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
```

2. Create a function to validate the email:

```
function validateEmail(email) {
  return emailPattern.test(email);
}
```
3. Use the validateEmail() function to validate an email address:
```
const email = "example@example.com";
const isValid = validateEmail(email);
console.log(isValid);  // Output: true
```
By following these steps, you can use the provided regular expression pattern in JavaScript to validate email addresses effectively in your web applications.



## Conclusion
Matching and validating email addresses using regular expressions can be a challenging task due to the various email formats allowed. The provided regular expression pattern serves as a starting point for basic email validation. However, it's important to consider specific requirements when implementing email validation in your application. Regular expressions offer a powerful tool for email validation, and by understanding the basics, you can customize the pattern to suit your specific needs.

## Author
 Written by Ellie Chayo, a web development student.  You can find more of Ellie's projects and contributions on her [GitHub repository](https://github.com/elliechayo)






