# extract-react-intl

[![Build Status](https://travis-ci.org/akameco/extract-react-intl.svg?branch=master)](https://travis-ci.org/akameco/extract-react-intl)
[![tested with jest](https://img.shields.io/badge/tested_with-jest-99424f.svg)](https://github.com/facebook/jest)
[![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![All Contributors](https://img.shields.io/badge/all_contributors-6-orange.svg?style=flat-square)](#contributors)

This package allows you to extract all messages from a glob. It will return an object with a key for each locale you pass, which in turn contains an object with the ids of each message defined by the [`defineMessages`](https://github.com/yahoo/react-intl/wiki/API#definemessages) function of [react-intl](https://github.com/yahoo/react-intl). The value of each of these keys will be an empty string, except for your `defaultLocale` which will be populated with the [`defaultMessage`](https://github.com/yahoo/react-intl/wiki/API#message-descriptor).

## Install

```
$ yarn add --dev extract-react-intl
```

## Usage

```js
const extractReactIntl = require('extract-react-intl')

const pattern = 'app/**/*.js'
const locales = ['en', 'ja']

extractReactIntl(locales, pattern).then(result => {
  console.log(result)
  /*
{
  en:
   { 'components/App/hello': 'hello',
     'components/App/welcome': 'welcome to extract-react-intl' }
  ja:
   { 'components/App/hello': '',
     'components/App/world': '' }
}
  */
})
```

## API

### extractReactIntl(locales, pattern, [options])

Return a `Promise` wrapped extracted messages.

#### locales

Type: `Array<string>`

Example: `['en', 'ja']`

#### pattern

Type: `string`

File path with glob.

#### options

Additional options.

#### defaultLocale

Type: `string`<br> Default: `en`

Set default locale for your app.

#### moduleSourceName

Type: `string`<br> Example: `./path/to/module` <br> Default: `react-intl`

The ES6 module source name of the React Intl package. Defines from where _defineMessages_, `<FormattedMessage />` and `<FormattedHTMLMessage />` are imported.

#### extractFromFormatMessageCall

Type: `boolean`<br> Example: `--extractFromFormatMessageCall` <br> Default: `react-intl`

If the value is `true`, Extractor will extract the i18n message and ID from `intl.formatMessage` calls as well.
i:e

```
intl.formatMessage({
                id: 'Supported.file.types',
                defaultMessage: 'Supported file types',
            })
```

##### cwd

Type: `string`<br> Default: `.`

**You most likely don't need this.**

Change run path.

## Contributors

Thanks goes to these wonderful people
([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
| [<img src="https://avatars2.githubusercontent.com/u/4002137?v=4" width="100px;" alt="akameco"/><br /><sub><b>akameco</b></sub>](http://akameco.github.io)<br />[💻](https://github.com/akameco/extract-react-intl/commits?author=akameco "Code") [📖](https://github.com/akameco/extract-react-intl/commits?author=akameco "Documentation") [⚠️](https://github.com/akameco/extract-react-intl/commits?author=akameco "Tests") [🚇](#infra-akameco "Infrastructure (Hosting, Build-Tools, etc)") | [<img src="https://avatars0.githubusercontent.com/u/27622?v=4" width="100px;" alt="nodaguti"/><br /><sub><b>nodaguti</b></sub>](http://about.me/nodaguti)<br />[💻](https://github.com/akameco/extract-react-intl/commits?author=nodaguti "Code") [⚠️](https://github.com/akameco/extract-react-intl/commits?author=nodaguti "Tests") | [<img src="https://avatars1.githubusercontent.com/u/11943024?v=4" width="100px;" alt="fix-fix"/><br /><sub><b>fix-fix</b></sub>](https://github.com/fix-fix)<br />[💻](https://github.com/akameco/extract-react-intl/commits?author=fix-fix "Code") | [<img src="https://avatars3.githubusercontent.com/u/1190640?v=4" width="100px;" alt="enrique-ramirez"/><br /><sub><b>enrique-ramirez</b></sub>](https://github.com/enrique-ramirez)<br />[📖](https://github.com/akameco/extract-react-intl/commits?author=enrique-ramirez "Documentation") | [<img src="https://avatars3.githubusercontent.com/u/1264276?v=4" width="100px;" alt="bradbarrow"/><br /><sub><b>bradbarrow</b></sub>](http://bradbarrow.com)<br />[🐛](https://github.com/akameco/extract-react-intl/issues?q=author%3Abradbarrow "Bug reports") [💻](https://github.com/akameco/extract-react-intl/commits?author=bradbarrow "Code") [⚠️](https://github.com/akameco/extract-react-intl/commits?author=bradbarrow "Tests") | [<img src="https://avatars1.githubusercontent.com/u/4540538?v=4" width="100px;" alt="Filip Filson Pasternak"/><br /><sub><b>Filip "Filson" Pasternak</b></sub>](https://github.com/Filson14)<br />[💻](https://github.com/akameco/extract-react-intl/commits?author=Filson14 "Code") |
| :---: | :---: | :---: | :---: | :---: | :---: |

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the
[all-contributors](https://github.com/kentcdodds/all-contributors)
specification. Contributions of any kind welcome!

## License

MIT © [akameco](http://akameco.github.io)
