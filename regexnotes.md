# Regex Reference
**by Rashaud Teague**

**NOTES**

First, this list will always be appended or updated...

Use all with the appropriate flags/modifiers, word bounderies, and ^...$
I mention that a few examples "... are valid", are really just a few examples

## Table of Contents
* [Phone Numbers](#phone-numbers)
* [URLs](#urls)
* [Email addresses](#email-addresses)
* [Date Format](#date-format)
* [Time Format](#time-format)
* [U.S. Currency](#us-currency)
* [Other](#other)

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
**Common url, break down the third match group afterwards for further validation**
```
https?://(?!\.|-)((?:\.?[-a-z0-9]+)+)(:[0-9]{1,5})?(/\S*)?
```

## Email addresses
**email address**
```
([a-z0-9][-a-z0-9._+]+)@(?!\.|-)((?:\.?[-a-z0-9]+)+)
```

## Date Format
**The most common date format in the U.S.; would match MM/DD/YYYY, or M/D/YY, or any combination of both; or MM/DD, or MM/YYYY. All forward slashes you see in the regex can be subsituted with dot '.' or dash '-' characters run true with this format: MM.DD.YYYY**

**And you can flip the month and day group '()' positions in the regex for a DD/MM/YYYY format...**
```
\b(0(?=[1-9])[0-9]|[1-9]|1[02]?)(?:/(0(?=[1-9])[0-9]|3(?=[01])[01]|[12]?[0-9]))?/([0-9]{2,4}(?!/))\b
```
**Common date format. Would match: Feb 30th 1987 or February 28th, 2000 or Feb 2220**

**The day and month groups '()' can be flipped for the example date: 5 Aug 2017**
```
\b(Jan|January|Feb|February|Mar|March|Apr|April|May|Jun|June|Jul|July|Aug|August|Sep|September|Oct|October|Nov|November|Dec|December)\b *(3(?=[01])[01]|[12]?[0-9])?(?:st|nd|rd|th)?,? *([0-9]{4})
```
**Same as above, but with just a 2-digit year
```
\b(Jan|January|Feb|February|Mar|March|Apr|April|May|Jun|June|Jul|July|Aug|August|Sep|September|Oct|October|Nov|November|Dec|December)\b *(3(?=[01])[01]|[12]?[0-9])?(?:st|nd|rd|th)?,? *([0-9]{2})
```
## Time Format
Common time formats, the ones you are likely to see everyday for capturing time zones, you could open a file with a list of them or have an array in-code then format a string with a time format regular expression with timezones in a matching group.

An example:<timeregex> *(ET|CST|MT|...)?

Replace <timeregex> with the relevant time regex you see below or whatever...

**time format: 12:00pm, 9:00 are valid**
```
\b(1(?=[012])[012]|[1-9]):([0-5][0-9])( ?[ap]m)?
```
**time format: 1230pm, 12pm are valid**
```
\b(1(?=[012])[012]|[1-9])([0-5][0-9])?( ?[ap]m)
```
*NOTE: Refer to ISO 8601 for the time formats below* 

**time format: 1459, 145952, 145952Z are valid**
```
^(2[0-4]|[01][0-9])([0-5][0-9])(60|[0-5][0-9])?(?: ?(Z|UTC))?$
```
**time format: 1459+24, 145952-02:22, 145952+2259 are valid**
```
(2[0-4]|[01][0-9])([0-5][0-9])([0-6][0-9])?((?:\+|-)(2[0-4]|[0-1][0-9])(:?[0-5][0-9])?)?
```
**time format: 22:32:09, 09:00, 12:59:59Z, 06:00 UTC are valid**
```
(2[0-4]|[01][0-9]):([0-5][0-9])(:(?:60|[0-5][0-9]))?(?: ?(Z|UTC))?
```
**time format: 22:32:09+23, 09:00-1233 are valid**
```
(2[0-4]|[01][0-9]):([0-5][0-9])(:[0-6][0-9])?((?:\+|-)(2[0-4]|[0-1][0-9])(:?[0-5][0-9])?)?
```

## U.S. Currency
**No thousands separator**
```
\$([0-9]+)(?:\.([0-9]{1,2}))?(k|m|b|t)?
```
**With thousands separator**
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

