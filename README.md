
# Apiary

![Logo](https://w3c.github.io/apiary/logo.svg)

Apiary is a simple JavaScript library to leverage the W3C API.
This library is intended to be used from W3C pages: domain pages, group pages, personal pages, etc.
With Apiary, you can inject data that is retrieved using the W3C API, in a declarative way using *placeholders*.
Examples are also provided.

Refer to [the W3C API](https://github.com/w3c/w3c-api) and [its documentation](https://w3c.github.io/w3c-api/) for details.

## Live examples

* [*Domain page*](https://w3c.github.io/apiary/examples/domain.html)
* [*Group page*](https://w3c.github.io/apiary/examples/group.html)
* [*User page*](https://w3c.github.io/apiary/examples/user.html)

## Getting started

1. Include [jQuery](http://jquery.com/) and [Apiary](apiary.js) in your page:
```html
<script src="//www.w3.org/scripts/jquery/2.1.4/jquery.min"></script>
<script src="//w3c.github.io/apiary/apiary.js"></script>
```
2. Specify your W3C API key, adding a *data-api-key* attribute to the HTML element, eg:  
```html
<html data-api-key="abc123def456">
```
You can get an API key very easily; refer to [the documentation](https://w3c.github.io/w3c-api/#apikeys).
(The examples provided here work with an API key that is intended only for testing Apiary.)

3. Specify the ID of the *entity* you want, adding a *data-&#42;* attribute to a container element, eg:  
```html
<main data-domain-id="41381">
```

4. Finally, add *placeholders* wherever you want real data about that *entity*, eg:  
```html
The lead of this domain is: <span class="apiary-lead"></span>.
```

## Reference

The container element should have *one* of these *data-&#42;* attributes, and its value should be a valid ID:
* `data-domain-id`
* `data-group-id`
* `data-user-id` (use [the user hash](https://api-test.w3.org/doc#get--users-{hash}))

A placeholder is any element with a class beginning with `apiary-`.
Bear in mind that a new chunk of DOM will be inserted there; whatever that placeholder contains will be lost.
We recommend that you have something in there giving users a hint that data is being loaded dynamically.
For example:
```html
<div class="apiary-chairs">[Loading…]</div>
```

For consistency (and to adhere to the [POLA](https://en.wikipedia.org/wiki/Principle_of_least_astonishment)),
the suffix part of these placeholders is equal to [the object keys returned by the API](https://api-test.w3.org/doc).

These are all the supported placeholders now:

Placeholder             | Applies to             | Generated content
:-----------------------|:-----------------------|:-----------------
`apiary-activities`     | domains                | `<ul>`
`apiary-chairs`         | groups                 | `<ul>`
`apiary-description`    | groups                 | text
`apiary-family`         | users                  | text
`apiary-given`          | users                  | text
`apiary-lead`           | domains                | text
`apiary-name`           | domains, groups, users | text
`apiary-photo` ¹        | users                  | `<img>`
`apiary-specifications` | users                  | `<ul>`
`apiary-type`           | groups                 | text

¹ Largest size returned by the API, if there are several.

The additional class `apiary` in the example files is ignored by Apiary itself but you may wish to include it anyway to all placeholders in your documents for easier CSS styling.

## Credits

Copyright © 2015 [World Wide Web Consortium](http://www.w3.org/)

This project is licensed [under the terms of the MIT license](LICENSE.md).

