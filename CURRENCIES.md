CURRENCIES
==========

This document contains my notes from working with multiple currencies in a single checkout system.

### Sources of Experience

- Nexleader Licensing Partner Support

### ISO 4217

From Wikipedia:

>The ISO 4217 code list is used in banking and business globally. In many countries the ISO codes for the more common currencies are so well known publicly that exchange rates published in newspapers or posted in banks use only these to delineate the currencies, instead of translated currency names or ambiguous currency symbols. ISO 4217 codes are used on airline tickets and international train tickets to remove any ambiguity about the price.

[Full Wikipedia Article on ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)

### Currency Data Model

|Field     |Type                            |Example|Description                                                         |
|----------|--------------------------------|-------|--------------------------------------------------------------------|
|Code      |3-Letter Case-insensitive String|USD    |A unique code that identifies the currency                          |
|Number    |A 3-Digit Number                |840    |A unique code that identifies the currency                          |
|E/Fraction|An integer                      |2      |The number of digits typically displayed after the decimal separator|

### Falsehoods about Currencies

- Everybody uses the United States Dollar
- Every country issues its own currency
- Every country uses the currency its government issues
- Every currency is issued by a government
- Every business uses the currency of the government where it operates
- Every displayed currency value should be followed by two decimal places
- Every browser supports every currency symbol
- The difference between Canadian Dollars and US Dollars is obvious without the use of labels
- Changing currencies is free
- Currencies will be changed at a "fair" exchange rate by your payment provider
- Your bank will always hold any currency you collect
- Your bank will never hold foreign currency for you
- Your bank will understand that a check was written in foreign currency not their local currency
- The currency you are working with is atomic
- The currency you are working with is not atomic
- The country you are working in will continue to use the same currency forever
- Your client will want to charge everybody the same price for the same product
- Your client will want to charge everybody in the same currency
- Your client understands the tax and accounting implications of working with foreign currency