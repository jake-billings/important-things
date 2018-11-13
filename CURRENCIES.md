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

Note that ISO 4217 standardizes _currency codes_ *not* _country codes_. Country codes are standardized by [ISO 3166-1](https://en.wikipedia.org/wiki/ISO_3166-1).

Country code and currency code must be separate fields in a database if both must be stored.

### JSON List of Currencies

After some research, I found this npm package, which provides a list of currencies and symbols in JSON. I like this one the best. It has regular downloads and multiple contributors.

https://www.npmjs.com/package/currency-format

If you're using this in the future, make sure that active contributions are still being made.

### Possible Model for Rendering Currencies

- Host a REST endpoint on your backend similar to `/api/currencies/:currencyCode`.
- Build a view component that accepts two parameters `currencyCode` and `currencyQuantity`. Alternatively, you could have a `price` type with those two fields.

The view component is responsible for loading metadata about the currency code and using it to render `currencyQuantity` as the proper quantity.

This approach drastically reduces the overhead on the frontend. It doesn't need to store a currency database. However, it requires an easily-cached REST request every time you render a currency.


### Falsehoods about Currencies

- Everybody uses the United States Dollar
- Every country issues its own currency
- Every country uses the currency its government issues
- Every currency is issued by a government
- Every currency expects the money symbol on the left-hand side of the quantity
- Every currency symbol is a single UTF-8 character
- Every currency has a unique symbol
- Every currency people use is listed in ISO 4217
- Bitcoin is not listed in your ISO 4217 library
- Bitcoin is ISO 4217 approved
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
- You understand the tax and accounting implications of working with foreign currency
- Your currency data/library is up-to-date with the real world

### Professional Expertise

I always recommend having a Certified Public Accountant (CPA) review the flow of funds through any payment procession system before going live. Small mistakes in payment processing can create huge liabilities for a business. This is especially important for platform-type projects.