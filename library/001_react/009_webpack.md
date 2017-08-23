# webpack配置
## webpack
### webpack.config.js
```javascript
const webpack = require('webpack');
const path=require("path");
module.exports={
  entry:{
      index:path.resolve("./dev/index.jsx"),
  },
  output:{path:path.resolve("./www/js"),filename:"[name].js"},
  module:{
      loaders: [{
          test: /\.js[x]?$/,
          exclude: /node_modules/,
          loader: 'babel-loader?presets[]=es2015&presets[]=react'
      }]
  },
  plugins: [
    new webpack.DefinePlugin({
      'process.env': {
        'NODE_ENV': JSON.stringify('production')
      }
    }),
    new webpack.optimize.UglifyJsPlugin({
      compress: {
        warnings: false    
      }
    })
    // new webpack.SourceMapDevToolPlugin({
    //   // Match assets just like for loaders.
    //   test: string | RegExp | Array,
    //   include: string | RegExp | Array,
    //
    //   // `exclude` matches file names, not package names!
    //   exclude: string | RegExp | Array,
    //
    //   // If filename is set, output to this file.
    //   // See `sourceMapFileName`.
    //   filename: string,
    //
    //   // This line is appended to the original asset processed. For
    //   // instance '[url]' would get replaced with an url to the
    //   // sourcemap.
    //   append: false | string,
    //
    //   // See `devtoolModuleFilenameTemplate` for specifics.
    //   moduleFilenameTemplate: string,
    //   fallbackModuleFilenameTemplate: string,
    //
    //   module: bool, // If false, separate sourcemaps aren't generated.
    //   columns: bool, // If false, column mappings are ignored.
    //
    //   // Use simpler line to line mappings for the matched modules.
    //   lineToLine: bool | {test, include, exclude}
    // })
  ]
};
```
### 监测
- 只能监测一个js
`webpack -w index.jsx index.js`
- 可监测多个js，在入口和出口之间调用模块的loaders
`webpack -w`

## webpack-dev-server
```
npm install webpack-dev-server -g
webpack-dev-server -w
```
在地址栏复制http:...........webpack-dev-server<br>
一旦改变，监测到页面也会刷新
