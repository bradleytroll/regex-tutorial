# Credit Card Number Validation Regex 

A quick regex code to verify credit card numbers for various card types/companies. 

## Summary

This gist focuses on how the following regex works, validating FINISH

```
/^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14}|3[47][0-9]{13}|3(?:0[0-5]|[68][0-9])[0-9]{11}|6(?:011|5[0-9]{2})[0-9]{12}|(?:2131|1800|35\d{3})\d{11})$/
```

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

The '^' anchor indicates the beginning of a string, while the '?' anchor indicates the end. The search will include the entire string within these anchors. 

### Quantifiers

The following quantifiers are used in this regex, primarily for validating various types of credit cards:
- Visa Validation
    - `{12}` indicates there should be exactly 12 occurances of the preceding element '[0-9]', verifyting the number length.
    - `{3})?` the use of the '?' indicates the three numbers specified by '[0-9]{3}' may or may not be present, allowing for numbers both 13 and 16 digits long. 
- MasterCard Validation
    - `{14}` indicates there should be exactly 14 occurances of the preceding element '[0-9]', ensuring a 16-digit number that begins with 51-55.
- American Express Validation
    - '{13}' indiciates there should be exactly 13 occurances of '[0-9]', ensuring a 15-digit card number.
- Diner's Club Validation
    - '{11}' indicates there should be exactly 11 occruances of '[0-9]', 

### OR Operator

The OR Operator is used throughout this regex to separate different credit card companies based on the patterns of each specific card type.

### Character Classes

Most character classes are bracket expressions, which will be discussed in a following section. 
- '\d' indicates any digit between 0 and 9 (same as the bracket expression '[0-9]')

### Grouping and Capturing

- '(?:4[0-9]{12}(?:[0-9]{3})?)' groups the validation pattern for Visa cards. The outer parentheses capture the full match, while the inner '?:' are non-capturing groups. The final non-capturing group supports both 13 and 16 digit card numbers.
- '(?:0[0-5]|[68][0-9])' groups the validation patthern for Diner's Club cards that begin with '30' and are followed by a number from 0 to 5 or begin with '36' or '38' followed by any number. 
- '(?:011|5[0-9]{2})' groups the validation pattern for Disover cards that begin with '6011' or '65' followed by any two numbers.
- '(?:2131|1800|35\d{3})' groups the validation pattern for JCB cards that begin with '2131', '1800', or '35' followed by any three numbers.

### Bracket Expressions

- '[0-9]' matches any digit between 0 and 9
- '[1=5]' is used for the MasterCard validation to ensure the card number begins with a digit between 1 and 5.
- '[0-5]' is used for the Diner's Club validation to ensure the third digit of the card number is 0-5. In the context of the code, this ensures the card numubers begin 300-305.
- '[68]' is used for the Diner's Club validation to ensure a valid third digit for nubmers that begin '36' or '38'.

### Greedy and Lazy Match

- Greedy Quantifiers
    - '[0-9]{12}' is used for Visa validation is greedy, matching exactly 12 digits.
    - '[0-9]{14}' is used for Mastercard validation is greedy, matching exactly 14 digits.
    - '[0-9]{13}' is used for American Express validation is greedy, matching exactly 13 digits.
    - '[0-9]{11}' is used for Diner's Club validation is greedy, matching exactly 11 digits.
- Lazy Quantifiers
    - '[0-9]{3}?' is used for the optional trailing digits in the Visa validation pattern. The '?' makes the quantifier lazy, matching between 0 and 3 digits, making this group of digits optional, allowing for the card number to be either 13 or 16 digits. 

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
