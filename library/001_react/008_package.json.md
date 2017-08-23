# package.json 项目配置文件
## 创建项目配置文件
`npm init`
## 下载依赖项
- 开发环境下依赖项
`npm install xxx --save`
- 发布后依然依赖的项
`npm install xxx --save-dev`
- 如果配置文件中已写好依赖项，下载所有依赖项
`npm install`


## package.json
```json
{
  "name": "",
  "version": "1.0.0",
  "main": "",
  "license": "MIT",
  "dependencies": {
    "body-parser": "^1.15.2",
    "react-redux": "^4.4.6",
    "redux": "^3.6.0",
  },
  "devDependencies":{
    "babel-core": "^6.18.2",
    "babel-loader": "^6.2.8",
    "babel-preset-es2015": "^6.18.0",
    "babel-preset-react": "^6.16.0",
    "react": "^15.4.1",
    "react-dom": "^15.4.1",
    "webpack": "^1.14.0"
  }
}
```
