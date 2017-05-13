# Regex Reference
**by Rashaud Teague**

## NOTES&*()@!™¢∞§*&&^%!2#test%20tag-ha:
Use all with the appropriate flags/modifiers, word bounderies, and ^...$
I mention that a few examples "... are valid", are really just a few examples

## Table of Contents
1.[Phone Numbers](#phone-numbers)

## Phone Numbers
**phone number 1 non-country code, U.S.**
```
(?:1(?: |-)?)?(\(?[0-9]{3}\)?)(?:-| )?([0-9]{3})-([0-9]{4})
```
**phone number match 2**
```
1?[1-9][0-9]{9}
```

## URLs
**Common url - break down the third matching (/\S*)? group afterwards for further validation**
```
https?://(?!\.|-)((?:\.?[-a-z0-9]+)+)(:[0-9]{1,5})?(/\S*)?
```

## Email addresses
**email address**
```
([a-z0-9][-a-z0-9._+]+)@(?!\.|-)((?:\.?[-a-z0-9]+)+)
```

## Date Format

## Time Format
Common time formats, the ones you are likely to see everyday for capturing time zones, you could open a file with a list of them or have an array in-code then format a string with a time format regular expression with timezones in a matching group.

An example:<timeregex> ?(ET|CST|MT...)?

Of course replace <timeregex> with the relevant time regex you see below or whatever...

**time format: 12:00pm, 9:00 are valid**
```
(1[0-2]|[1-9]):([0-5][0-9])( ?[ap]m)?
```
**time format: 1230pm, 12pm are valid**
```
(1[0-2]|[1-9])([0-5][0-9])?( ?[ap]m)
```
*NOTE: Refer to ISO 8601 for the time formats below* 

**time format: 1459, 145952, 145952Z are valid**
```
(2[0-4]|[0-1][0-9])([0-5][0-9])([0-6][0-9])? ?(Z|UTC)?
```
**time format: 1459+24, 145952-02:22, 145952+2259 are valid**
```
(2[0-4]|[0-1][0-9])([0-5][0-9])([0-6][0-9])?((?:\+|-)(2[0-4]|[0-1][0-9])(:?[0-5][0-9])?)?
```
**time format: 22:32:09, 09:00, 12:59:59Z, 06:00 UTC are valid**
```
(2[0-4]|[0-1][0-9]):([0-5][0-9])(:[0-6][0-9])? ?(Z|UTC)?
```
**time format: 22:32:09+23, 09:00-1233 are valid**
```
(2[0-4]|[0-1][0-9]):([0-5][0-9])(:[0-6][0-9])?((?:\+|-)(2[0-4]|[0-1][0-9])(:?[0-5][0-9])?)?
```

## U.S. Currency
```
\$([0-9]+)(?:\.([0-9]{1,2}))?(k|m|b|t)?
```
```
\$([0-9]{1,3})(?:(?:,?(?:[0-9]{3}))+)?(?:\.([0-9]{1,2}))?
```

## Other

**Digits, replace `<n>` with a number, for example: [0-9]{4}**
```
[0-9]{<n>}
```

**Floats, `<bit-precision>` should be replaced with 2,4,8,16,32,64,128,256, or whatever number you please**
```
[0-9]+(?:\.[0-9]{1,<bit-precision>})?
```

