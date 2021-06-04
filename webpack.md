# webpack

```js

// dist에서 index.html 주변에
// <img src="./images/logo.png" alt="HEROPY" />
// 상대경로를 인식하기 위해서 패키지를 설치
$ npm i -D copy-webpack-plugin

// webpack.config.js에서 import
const CopyPlugin = require('copy-webpack-plugin')


// plugins의 요소로 입력해준다.

 new CopyPlugin({
      patterns: [
        { from: 'static' }
      ]
    })



```
---

# css loader

```plaintext

webpack은 css를 읽을 수 없기 때문에 그것을 위한 패키지를 설치한다.

```
```js
$ npm i -D css-loader style-loader


// webpack.config.js

  module:{
    rules:[
      {
        test:/\.css$/,
        use:[
          'style-loader', 
          'css-loader' 
          // css-loader이 style-loder보다 먼저 읽힌다.  
          // js에서 css 파일을 해석하기 위해서 사용
          // style-loader가 html 부분에서 style 태그로 삽입
          // 순서 무적이나 중요   
        ]
      }
    ]
  }

```

# scss-loader

```js
$ npm i -D sass-loader sass

module:{
    rules:[
      {
        test:/\.s?css$/,
        use:[
          'style-loader',
          'css-loader',
          'sass-loader'// 여기 추가
        ]
      }
    ]
  }
```

# Autoprefixer(PostCSS)
```js

$ npm i -D postcss autoprefixer postcss-loader

//package-json에 해당 코드를 입력

"browserslist":[
    "> 1%",
    "last 2 versions"
  ]


// .postcssrc.js 생성
module.exports = {
  plugins: [
    require('autoprefixer')
  ]
}


```

# babel

```js
$ npm i -D @babel/core @babel/preset-env @babel/plugin-transform-runtime

// .babelrc.js 파일 생성
module.exports = {
  presets:['@babel/preset-env'],
  plugins: [
    ['@babel/plugin-transform-runtime']
  ]
}

// webpack.config.js 파일에서 module부분에 해당 코드 추가

      {
        test: /\.js$/ ,
        use:[
          'bable-loader'
        ]
      }
// 그 후, babel-loader를 추가 설치하면 Babel 구성은 끝
$ npm i -D babel-loader

```