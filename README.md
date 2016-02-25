# graphql-knex

[![NPM version][npm-image]][npm-url]
[![Build status][ci-image]][ci-url]
[![Dependency Status][daviddm-image]][daviddm-url]
[![Code Climate][codeclimate-image]][codeclimate-url]

GraphQL -> Knex.

## Install

```sh
$ npm install --save graphql-knex
```

## Usage

```js
const Query = require('graphql-knex').Query
const knex = require('knex')({
  client: 'pg',
  connection: {
    // ...
  }
})

const gqlQueryString = `
  query favoriteColorQuery ($name: String!) {
    person(name: $name) {
      favoriteColor
    }
  }`

const gqlQuery = new Query(gqlQueryString)
gqlQuery.toKnexQuery(knex)
  .then(person => {
    console.log(person.favoriteColor)
  })
```

[npm-image]: https://img.shields.io/npm/v/graphql-knex.svg?style=flat-square
[npm-url]: https://npmjs.org/package/graphql-knex
[ci-image]: https://img.shields.io/travis/tjwebb/graphql-knex/master.svg?style=flat-square
[ci-url]: https://travis-ci.org/tjwebb/graphql-knex
[daviddm-image]: http://img.shields.io/david/tjwebb/graphql-knex.svg?style=flat-square
[daviddm-url]: https://david-dm.org/tjwebb/graphql-knex
[codeclimate-image]: https://img.shields.io/codeclimate/github/tjwebb/graphql-knex.svg?style=flat-square
[codeclimate-url]: https://codeclimate.com/github/tjwebb/graphql-knex

