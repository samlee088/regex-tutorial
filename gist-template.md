# Email Validation with Regex Expression

Hello~!

This regular expression tutorial was created to help teach about [regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) (regex). In terms of Javascript, regex are used to help identify information in a string, and can validate if a particular pattern is included in the string.

For example, in the following example string, regex can be used to validate if the following string contains numbers, where either one of the two listed here can be used:

- example string : masterChief343PacificNorthWest

- example regex expression : [0-9]

- return : true - The regex expression was used to determine if the example string contained a number

We will go in further detail about the particular syntax for these coming up, however we wanted to start off by giving a simple example and how regex expressions can be used.

It if also important to note here that regex expressions are case sensitive unless directed otherwise.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

In this regex guide, we will be going over an example regex expression that can be used to match an email address. We go over the individual components that can be used to create a regex pattern, and then how these can be tied together to create a regex for email recognition.

Matching an Email – `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)
- [Recap](#recap)

## Regex Components

### Anchors

Anchors are used to determine the positions, rather than character values. For example, they can be used to denote the beginning of a string, or the end of a text.

Examples:

- ^ : Used to reference the starting position, or beginning of a string or line.

  - An example of this is `^video` where the string `video games are fun` returns `true`.

- $ : Used to reference the ending position, or ending of a string or line.

  - An example of this is `challenging` where the string `deadlifts are challenging` returns `true`

- Email regex: We are using the start and end anchors to specify if the email the beginning and ending pattern recognition.

  - `^([a-z0-9_\.-]+)` : The beginning anchor is being used to specify the pattern recognition for the start of the email address.
  - `([a-z\.]{2,6})$` : The ending anchor is being used to specify the pattern recognition for the end of the email address.

### Quantifiers

Quantifiers are used to specify the count of pattern recognition. They can be used to reference the number of repeating patterns, or the mix and maximum limit of a character pattern.

Examples:

- {n} : Used to match exactly n times

  - An example of this is `[0-9]{2}` where the string `There are 42 bottles of beer on the wall` would return `42` with a search return.

- {n, } : Used to specify lower limit of n

  - An example of this is `[a-z]{3}` where the string `by` would return `false` due `by` being only 2 characters long.

- Email regex : The Quantifiers in this case are in reference to the `{2,6}` which specifies that the characters after the `.` include lower case numbers, special character `.` and are in 2-6 characters in length.
  Additionally there is usage of a Quantifier with the `+` which specifies a minimum match of 1, and an maximum of infinity.

  - `([a-z\.]{2,6})` : valid if there are 2 to 6 characters containing lower case letters, or special character `.` .
  - `([a-z0-9_\.-]+)` : valid if there are at least one lower case letters, or special characters `[ _ . -]` up to length infinity
  - `([\da-z\.-]+)` : valid if there are at least one lower case letters, numbers, or special characters `[ . -]` up to length infinity. Please note `\d` to be covered in section coming up.

### Grouping Constructs

Grouping Constructs are used to group together sections of regex to group together different patterns. Groupings can result in different interpretations of the regex expressions and can be used to give the proper intended results.

Examples:

- `javascript+` : This would look for expressions with `javascript` with any number of the character `t`, ie `javascript, javscriptt, javascripttt`
- `(javascript)+` : This would look for expressions with multiple repeat of the whole character string, ie `javascript, javascriptjavascript,      javascriptjavascriptjavascript`

- Email regex: The following groupings can be found in the email regex that are used to specify different patterns:

  - `^([a-z0-9_\.-]+)` : the `+` quantifier is being applied to the whole grouping here to look for the start of an email string with characters with any of the specified characters in the grouping
  - `([\da-z\.-]+)` : the `+` quantifier is being applied to the whole grouping here to look for the start of an email string with characters with any of the specified characters in the grouping
  - ([a-z\.]{2,6})$ : this grouping is being used to specify the pattern recognition for the end of the email

### Bracket Expressions

Brackets are used to specify particular sets of patterns to match. The most common usage of this are individual character list, or ranges of characters. Within a bracket expression, multiple characters or ranges can be specified.

Examples:

- `[abcde]` : This is used to look for a character that includes any of the characters `abcde`. Without a quantifier, this will search for the first instance. This will return a false for the expression `string`
- `[a-z0-9]` : This is used to look for a lower case letter or number. This will return a true for `apple`, or `apple6`

- Email regex: The following bracket expressions are used to specify different character acceptance in the different groupings.

  - `^([a-z0-9_\.-]+)`: This bracket expression combined with the quantifier and anchor specifies the pattern of any string with minimum length 1 and maximum infinity containing any lower case letters, numbers, and/or any of the special characters listed, positioned at the beginning of the email string.
  - `[\da-z\.-]+` : This bracket expression is used to specify any digit, lower case letter, and the special characters listed. With the quantifier it is for any string with the specified characters with length at least 1, maximum infinity. \*`([a-z\.]{2,6})$` : This bracket expression combined with the quantifier and anchor specifies the pattern of any string with minimum length 2 and maximum 6 containing any lower case letters and/or any of the special characters listed, positioned at the end of the email string.

### Character Classes

Character classes are a way to matches the characteristic from a specified set. A set can be for example letters, or digits.

Examples:

- `/w` : This is used to match any alphanumeric character, which is same as the bracket expression [A-Za-z0-9_].

- Email regex:

  - `\d` : This is used to match any digit, which is same as the bracket expression [0-9]. -`([\da-z\.-]+)` : This grouping is used to check for a string length of at least 1, maximum infinity including lower case letters, numbers, and/or any of the special characters listed.

### Character Escapes

Character Escapes are used to specify special characters that have a predetermined usage within regex to be interpreted literally.

- Email regex:

  - `\.` : This character class is used to interpret the `.` as literally. For the email regex, it is used to specify character pattern searches before and after the `.` that would be expected with valid email address.

### Recap

Using all of the different regex expressions together, we can see how our example regex expression is being used to validate an email:

Matching an Email – `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

- `^([a-z0-9_\.-]+)@` : The beginning of a string can include any of the following, lower case letters, numbers, or any of the special characters `[_ . -]` and must be of length at least 1 with no maximum limit. This beginning grouping is separated from the rest of the email address with the `@` symbol.
- `([\da-z\.-]+)\.` : The middle of the email address can include lower case letters, digits, or the special characters `[. -]` and must be of length at least 1 with no maximum limit. This middle grouping is separated from the ending grouping by the special character `.` .
- `([a-z\.]{2,6})$` : The ending of the email address can include lower case letters, and the special character `.` . The length of the string can be anywhere between 2 to 6 characters in length.

## Author

This was created by Samuel Lee. Additional information can be found [here](https://github.com/samlee088).
