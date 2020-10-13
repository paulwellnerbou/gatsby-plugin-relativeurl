# gatsby-plugin-relativeurl

[npm-url]:https://npmjs.org/package/gatsby-plugin-relativeurl
[npm-image]:https://img.shields.io/npm/v/gatsby-plugin-relativeurl.svg
[downloads-image]:https://img.shields.io/npm/dm/gatsby-plugin-relativeurl.svg
[david-dm-url]:https://david-dm.org/moxystudio/gatsby-plugin-relativeurl
[david-dm-image]:https://img.shields.io/david/moxystudio/gatsby-plugin-relativeurl.svg
[david-dm-dev-url]:https://david-dm.org/moxystudio/gatsby-plugin-relativeurl?type=dev
[david-dm-dev-image]:https://img.shields.io/david/dev/moxystudio/gatsby-plugin-relativeurl.svg

Adds support for deploying [Gatsby](https://www.gatsbyjs.com/) websites to subdirectories by ensuring that assets are relative.


## Installation

```sh
$ npm install --save gatsby-plugin-relativeurl
```


## Usage

Set `prefixPath` to `__GATSBY_RELATIVEURL_PATH_PREFIX__` and include the plugin in your `gatsby-config.js` file:

```js
module.exports = {
    pathPrefix: '__GATSBY_RELATIVEURL_PATH_PREFIX__',
    plugins: [
        'gatsby-plugin-relativeurl',
    ],
};
```

And now, simply build the project with `npm run build -- --prefix-paths`. Better yet, set it by default in your `package.json`:

```json
"scripts": {
  "build": "gatsby build --prefix-paths"
},
```


## But how?

It turns out the Gatsby doesn't support relative paths. But I didn't gave up and came up with smart and ugly hacks to do so:

- Adds a post-build step that iterates over files and transforms every `__GATSBY_RELATIVEURL_PATH_PREFIX__` occurrence
- Adds a very small code snippet to every HTML page that defines the `__GATSBY_RELATIVEURL_PATH_PREFIX__` global based on the browser location


## License

[MIT License](http://opensource.org/licenses/MIT)
