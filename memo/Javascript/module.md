# 자바스크립트의 모듈

## 모듈시스템의 배경

초기의 자바스크립트 프로그램은 작은 단위의 규모로 시작됐습니다. 초기에 사용된 대부분의 스크립트는 독립적인 작업을 수행하고, 필요한 경우 웹 페이지에 약간의 상호 작용을 제공하므로 일반적으로 큰 스크립트가 필요하지 않았습니다.

그러나 최근 몇 년 동안 자바스크립트 프로그램을 필요에 따라 가져올 수 있는, 별도의 모듈로 분할하기 위한 매커니즘을 제공하는 것에 대해 생각하기 시작했습니다. 
node.js는 오랫동안 이러한 능력을 가지고 있었고, 모듈 사용을 가능하게하는 많은 자바스크립트 라이브러리와 프레임워크가 있습니다.

* RequireJs
* CommonJS
* AMD
* Webpack
* Babel

## 모듈이란?

모듈이란 여러 기능들에 관한 코드가 모여있는 하나의 파일로 다음과 같은 장점이 있습니다

* 유지보수성
  - 기능들이 모듈화 되어있으면, 의존성을 줄일 수 있고 수정해야할 코드양이 줄어든다
* 네임스페이스화
  - 자바스크립트에서 전역변수는 전역공간을 가지기 때문에 코드의 양이 많아 질수록 겹치는 네임스페이스가 많아질 수 있다. 그러나 모듈로 분리하면 모듈만의 네임스페이스를 가지기 때문에 그 문제가 해결된다.
* 재사용성
  - 모듈로 분리한 코드를 다른 파일에서 필요할 때마다 사용할 수 있습니다. 


## ES 모듈과 CommonJS 모듈의 차이

현재 활발히 사용되고 있는 모듈은 ES 모듈과 CommonJS 모듈 두 가지이므로 두가지 방법의 모듈 방식에 대해서 정리하겠습니다.

### CommonJS 모듈의 내보내기 방법

CommonJS 모듈 방식에서 모듈을 내보내는 방법은 한가지다. module.exports 객체를 조작하는 방법이다. 해당 객체에 프로퍼티를 추가하거나, 다른 객체로 치환하면 다른 모듈에서 가져와서 사용할 수 있다.

1. 내보내기

```javascript

module.exports.crop = function() {};
module.exports.rotate = function() {};

module.exports = {
    crop: function() {},
    rotate: function() {}
}

```

2. 가져오기

```javascript

var filter = require('filter');

filter.crop();
filter.rotate();

```

require() 함수 실행을 통해 가져온 모듈은 앞서 내보낸 module.export 객체를 받은 것처럼 동작한다.

## ES 모듈의 내보내기 방법

ES 모듈은 CommonJS 모듈과 다르게 두 가지 방법으로 내보낼 수 있다.

1. 이름 붙인 내보내기(Named Export)

```javascript
// filter.js
export const crop = function(){};
export const rotate = function(){};

```

```javascript
// 불러오는 파일
import { crop, rotate * as superRotate } from './filter'

crop();
rotate();

```

위의 예시처럼 여러개로 나눠서 내보낼수 있고, import문으로 그 모듈을 가져올 때는 반드시 export에서 정의한 모듈이름으로 가져와야 한다. ( 물론 가져온 이름의 변경은 가능하다)

2. 기본값 내보내기




### 출처

* [You dont'know js module](https://ui.toast.com/weekly-pick/ko_20190418/)
* [mozilla JavaScript modules](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)