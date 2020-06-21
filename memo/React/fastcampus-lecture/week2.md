# 컴포넌트 라이플 사이클

Component 생성 및 마운트(v16.3 버전 이하)

construcutor -> componentWillMount -> render(최초) -> componentDidMount

componentWillUnmount() {
    컴포넌트가 Unmount 되는 경우를 생각해서 사용한다

    1. 진행중인 api를 중지
    2. 타이머를 중지
}

컴포넌트가 리렌더링 될경우

1.componentWillReceiveProps
    setState를 할 경우, props와 state가 따로 넘어가지 않고 합쳐서 넘어감 ( props와 state 구별이 필요 ) 
2.shouldComponentUpdate
    
3.componentWillUpdate
4.render
5.componentDidUpdate

렌더를 할지안할지 결정한다
    
shouldComponentUpdate(){
    return true;
}

Component 라이프 사이클 변경( v 16.3)


render 이후에 dom에 부착하기전에 작동
getDerivedStateFromProps


