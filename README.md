# mini-program-loader

mini program loader for webpack, forked from [wxapp-boilerplate](https://github.com/cantonjs/wxapp-boilerplate), added support for Baidu smart app.

## Installation

```bash
yarn add -D @lucashc/mini-program-loader
```

## Usage

You may also need to use
[file-loader](https://github.com/webpack-contrib/file-loader) to extract files.

```js
{
  test: /\.wxml$/,
  include: /src/,
  use: [
    {
      loader: 'file-loader',
      options: {
        name: '[name].[ext]',
        useRelativePath: true,
        context: resolve('src'),
      },
    },
    {
      loader: '@lucashc/mini-program-loader-loader',
      options: {
        root: resolve('src'),
        enforceRelativePath: true,
      },
    },
  ],
}
```

##### Options

* `root` (String): Root path for requiring sources
* `enforceRelativePath` (Boolean): Should be true if you wish to generate a
  `root` relative URL for each file. **It is recommend to set to `true`**
* `publicPath` (String): Defaults to webpack
  [output.publicPath](https://webpack.js.org/configuration/output/#output-publicpath)
* `transformContent(content, resource)` (Function): Transform content, should
  return a content string
* `transformUrl(url, resource)` (Function): Transform url, should return a url
* `minimize` (Boolean): To minimize. Defaults to `false`
* All
  [html-minifier](https://github.com/kangax/html-minifier#options-quick-reference)
  options are supported

## License

MIT
