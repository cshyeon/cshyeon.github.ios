---
layout: post
title: "npm package 만들어 배포하기"
slug: "npm-package-making-and-publish"
date: 2019-04-01 14:26:28 +0900
categories: nodejs npm
---

자주 사용될법한 코드를 모듈로 만들어 npm에 배포하고 필요한 곳에서 npm install을 통해 만들었던 모듈을 사용할수 있다면
코드의 재사용성을 높일수 있을것이다.

- browser와 node에서 모두 사용가능한 npm 모듈 만들기(webpack + babel)
webpack으로 번들링 되기전, 소스코드에서 browser에서만 사용되는 코드와(.browser.js)
node.js에서만 사용되는 코드를(.js) 서로 분리 시킨다.

package.json에 "browser" 오브젝트를 선언하고 property에 키값은 node.js에서 사용하는 파일명, value로는 browser일때 치환되는 파일명을 입력한다.
```json
"browser": {
  "./lib/test.js": "./lib/test.browser.js"
},
```

webpack.config으로 browserConfig, nodeConfig을 따로 만들어 2개의 빌드파일을 생성한다.
`"./dist/bundle.js", "./dist/bundle.browser.js"`

번들링 된 파일도 package.json -> browser 오브젝트에 똑같은 방식으로 추가한다.
```json
"browser": {
  "./lib/test.js": "./lib/test.browser.js",
  "./dist/bundle.js": "./dist/bundle.browser.js"
},
```

package.json "main"은 node.js 기준으로 진입 파일을 설정해 놓는다.
```json
"main": "./dist/bundle.js",
```

