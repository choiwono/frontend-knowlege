# LifeCycle Methods with React Hooks

* 번역글입니다
* [원글](https://blog.carbonfive.com/2019/10/15/replacing-component-lifecycle-methods-with-react-hooks/)

리액트의 컴포넌트를 작성할 때, 라이프사이클 이벤트에 대해 엑세스가 필요한 경우가 있습니다.
마운트시 데이터 가져오기, 컴포넌트 언마운트시 clearn up, 컴포넌트 업데이트시 props 처리 등등

리액트 16.8부터는 오직 3개의 라이프사이클 메서드를 사용할 수 있습니다.
componentDidMount, componentDidUpdate, componentWillUnmount

![컴포넌트 라이프 사이클](https://blog.carbonfive.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-09-at-11.43.05-AM-970x367.png)

## React Hooks을 통한 활용

**ComponentDidMount**

Before(class 기반 컴포넌트)

```javascript

import from "react"

class Component extends React.Component {
    componentDidMount() {
        console.log("컴포넌트가 돔에 부착되기 전에 작동")
    }
}

```

After(함수형 기반 컴포넌트 with hooks)

```javascript

import React, { useEffect } from 'react';

const Component = () => {
    useEffect(() => {
        console.log("컴포넌트가 돔에 부착되기 전에 작동")
    }, [])
    return <div>hello</div>
}

```

**ComponentDidUpdate**

Before ( 클래스 기반 컴포넌트 )

```javascript

import React from "react";
 
class Component extends React.Component {
  componentDidUpdate() {
    console.log("컴포넌트가 새로운 props나 state를 받으면 작동");
  }
 
  render() {
    return <h1>Hello World</h1>;
  }
};

```

After(함수형 기반 컴포넌트 with hooks)

```javascript

import React, { useEffect } from "react";
 
const Component = ({ state }) => {
  useEffect(() => {
    console.log("컴포넌트가 새로운 props나 state를 받으면 작동");
  }, [state]);
 
  return <h1>Hello World</h1>;
};

```

state가 변경될때마다 작동한다.

**ComponentWillUnmount**

Before(class 기반 컴포넌트)

```javascript

import React from "react";
 
class Component extends React.Component {
  componentWillUnmount() {
    console.log("컴포넌트가 돔에서 제거되기전에 작동");
  }
 
  render() {
    return <h1>Hello World</h1>;
  }
};


```


After(함수형 기반 컴포넌트 with hooks)

```javascript

import React, { useEffect } from "react";
 
const Component = () => {
  useEffect(() => {
    return () => {
        console.log("컴포넌트가 돔에서 제거되기전에 작동");
    }
  }, []);
 
  return <h1>Hello World</h1>;
};

import React, { useEffect } from "react";

const Component = () => {
  useEffect(() => {
    const intervalId = setInterval(() => {
      document.title = `Time is: ${new Date()}`;
    }, 1000);
 
    return () => {
      document.title = "Time stopped.";
      clearInterval(intervalId);
    }
  }, []);
 
  return <h1>What time is it?</h1>;
};

```