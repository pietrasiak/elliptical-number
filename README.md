elliptical-number
====================

[![Build Status](https://travis-ci.org/laconalabs/elliptical-number.svg?branch=master)](https://travis-ci.org/lacona-labs/elliptical-number)

Elliptical phrases for numbers (Integer, Decimal, DigitString, Ordinal)

## Installation

```sh
npm install elliptical-number
```

## Usage

```js
/** @jsx createElement */
import { DigitString, Integer, Ordinal, Decimal } from 'elliptical-number'
import { createElement, compile } from 'elliptical'

const parse = new compile(
  <sequence>
    <Integer max={99} min={0} id='numBottles' />
    <literal text=' bottles of beer on the wall' />
  </sequence>
}

parse('73 bottles of beer on the wall')
/* [{
  words: [
    {text: '73', input: true, argument: 'number'},
    {text: ' bottles of beer on the wall', input: true}
  ],
  score: 1,
  result: {numBottles: 73}
}] */
```

## Reference

### `Integer`

Accepts integers specified numerically. These can be negative. Does not currently accept numbers that are spelled out, or numbers with thousands separators.

#### Result

`Number` - A numeric representation of the input number.

#### Props

- `argument`: `String` - The label text for this phrase. Defaults to `number`.
- `max`: `Number` - the highest acceptable integer. No limit by default.
- `min`: `Number` - the lowest acceptable integer. No limit by default.

### `DigitString`

Designed to accept strings that happen to contain numbers. This should be used in place of `Integer` for things like phone numbers, zip codes, and time markers. While these things are represented with digits, they do not technically represent numbers, and should be managed with strings.

Only accept digits. That is, all inputs will be strings that can be parsed as positive integers.

#### Result

`String` - the string the user entered.

#### Props

- `argument`: `String` - The label text for this phrase. Defaults to `number`.
- `max`: `Number` - the highest acceptable integer. No limit by default.
- `min`: `Number` - the lowest acceptable integer. Defaults to 0.
- `maxLength`: `Number` - the highest acceptable string length. No limit by default.
- `minLength`: `Number` - the lowest acceptable string length. Defaults to 1.

### `Ordinal`

Accepts numbers specified in ordinal form. That is, numbers like 1st, 3rd, 12th, 202nd, etc.

#### Result

`Number` - A numeric representation of the input number.

#### Props

- `argument`: `String` - The label text for this phrase. Defaults to `number`.
- `max`: `Number` - the highest acceptable integer. No limit by default.
- `min`: `Number` - the lowest acceptable integer. No limit by default.

### `Decimal`

Accepts a fixed-point decimal specified numerically. These can be negative. Leading zero is optional.

#### Result

`Number` - A numeric representation of the input number.

#### Props

- `argument`: `String` - The label text for this phrase. Defaults to `number`.
- `max`: `Number` - the highest acceptable decimal. No limit by default.
- `min`: `Number` - the lowest acceptable decimal. No limit by default.
