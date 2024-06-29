vue.js란?
=========
- 사용자 인터페이스를 구축하기 위한 프론트엔드 프레임워크
- 싱글페이지 애플리케이션(SPA, single page application) 을 쉽고 빠르게 제작 가능

# SPA란?
- 단일 페이지에서 최소한의 내용만 서버에서 받아와 동적으로 업데이트되도록 하는 개발 방식 
- 모델-뷰-컨트롤러(MVC) 설계 패턴 사용  
            → 시각적 요소와 비즈니스 로직, 사용자 인터페이스 분리해 개발 <br/>
            → 서로 영향을 주지 않고 수정이 가능함

<img src="https://developer.mozilla.org/ko/docs/Glossary/MVC/model-view-controller-light-blue.png" width=500 alt="MVC Model-View-Controller" />

- 모델 : 데이터, 비즈니스 로직을 담당
      서버에서 데이터를 가져와 처리, 데이터 상태 관리  
- 뷰 : 사용자에게 보여지는 시각적인 요소 담당 
     html, css, ui 컴포넌트 등으로 구성 , 데이터 표시와 사용자 이벤트 담당 
- 컨트롤러 : 사용자 입력 처리, 모델의 데이터 수정 후 뷰 갱신 
- SPA 예시 서비스 : 트위터 ( 타임라인 스크롤 시 최신 트윗 확인 기능 → 페이지 전황 없이 동적으로 데이터 업데이트 ) 
            
<img src="https://blog.kakaocdn.net/dn/1K1L3/btq9iAl2zLY/bCRlOtnLqnL60XK56fkab1/img.png" width=700 />

- 페이지를 이동하지 않고 필요한 데이터만 업데이트 
- 따라서 화면이 깜빡이지 않고 부드럽게 전환. 페이지 이동보다 속도가 빠른 게 장점
- 서버 서버의 부하 감소. 네트워크 대역폭(한 번에 전송 가능한 데이터양) 줄일 수  있음

# Vue.js 프레임워크 
- 동작방식: vue 인스턴스에 데이터를 바인딩하고 html요소에 v-접두사로 시작하는 디렉티브를 속성으로 추가해 dom 요소와 데이터를 연결함
**데이터 바인딩** 
vue 인스턴스의 데이터를 html요소에 연결하는 것. <br/>
html 요소에 데이터를 바인딩하면 데이터가 변경될 때 화면에 변경된 데이터가 표시됨 <br/>
<br/>
**디렉티브** <br/>
html 요소에 특정 동작을 적용할 때 사용하는 vue.js의 표기법 <br/>

- Vue는 MVVM 패턴으로 설계됨
    
  ***MVVM 패턴이란?***
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCiXz0%2FbtqBQ1iMiVT%2FstaXr7UO95opKgXEU01EY0%2Fimg.png" width=400/>

  - view - view model - model로 구성   
    - view : UI 표현   
    - view model : 뷰에 대한 상태와 동작 정의 및 모델과의 데이터 바인딩을 처리함.    
                 사용자 입력에 대한 이벤트 처리와 명령 실행    
      → 데이터 변경 시 자동으로 뷰에 반영, 사용자 입력이 데이터에 반영되는 **양방향 데이터 바인딩** 가능   
    

  Vue는 **템플릿 기반** 의 개발을 권장 (템플릿 : vue에서 컴포넌트를 구성하는 단위. html/css/js 코드 포함)

## Vue 인스턴스 
웹 애플리케이션을 Vue.js의 기능으로 구성하고 동작시킬 수 있도록 함 
생성자 함수로 만듬

```
<html>
    <div id="app">{{ message }}</div>
</html>
<script>
    new Vue({
        el :"#app",
        data: {
            message: "Hello Vue.js!", 
        },
    });
</script>
```

### Vue 인스턴스 주요 속성 
- el: Vue 인스턴스를 연결할 html 요소   
- data: Vue 인스턴스가 관리하는 데이터   
- template: 화면에 표시할 요소   
- props: 부모 컴포넌트의 데이터를 받을 수 있는 속성   
- methods: 화면의 동작과 이벤트 로직을 제어하는 메서드  
- computed: Vue 인스턴스의 계산된 속성 

### Vue인스턴스의 생명주기

생명주기:  미리 정의된 과정을 거쳐 컴포넌트를 생성하고 웹 브라우저에 출력하는 과정 

-인스턴스의 생성, 소멸로 진행이 되는데, 이때 8개의 **생명주기 훅(콜백함수)** 을 제공함 

-생명주기 훅을 통해 데이터 초기화, 이벤트 제어 등의 작업을 처리함.

<img src="https://ko.vuejs.org/assets/lifecycle._trByeii.png" width=400/>
실행 과정
1. setup() 실행   <br/>
2. beforCreate 훅 실행    <br/>
3. 초기화,만들어지는 데이터, 반응성 생성 및 주입   <br/>
4. created 훅 실행    <br/>
5. 분기 처리. 컴파일된 템플릿이 있는지에 따라 달라짐    <br/>
    - template속성이 존재 : 해당 html 문자열을 템플릿으로 사용   <br/>
    - template속성이 존재 x: el 속성으로 지정된 dom 요소의 내부 html을 템플릿으로 사용   <br/>
6. beforeMount 훅 실행    <br/>
7. 초기 렌더링이 되면서 dom노드를 생성하고 인스턴스를 삽입함. <br/>   
8. mounted 훅 실행    <br/>
9. dom 요소에 vue인스턴스가 추가됨.(마운트 완료)   <br/> 
    9-1. 데이터 변경 시    <br/>
    1.beforeUpdate 훅 실행    <br/>
    2.화면 리렌더링 및 데이터 갱신    <br/>
    3.update 훅 실행    <br/>
10. 컴포넌트 마운트 해제 시     <br/>
    1.beforeUnmount 훅 실행    <br/>
    1. 컴포넌트 언마운트    <br/>
11. unmounted 훅 실행    <br/><br/>

<br/>
**setup() 이란?**
 컴포넌트의 데이터를 정의하고, 로직을 구성함.    
기존 options API는 다르게 단일 함수 내에서 모든 로직을 작성할 수 있게 해줌.    
컴포넌트 인스턴스가 생성되기 전에 실행되기 때문에, 인스턴스 접근이 필요한 기능은 사용할 수 없음   
setup() 보다는 <script setup> 문법이 권장된다.   


#### 8가지 훅
**beforeCreate** 
vue 인스턴스가 생성되고 초기화되기 전에 호출. 

컴포넌트가 DOM에 추가되기 전이기 때문에 template 안에 작성된 내용에 접근할 수 없음 

데이터와 이벤트에 대한 초기 설정 가능 

**created**

vue 인스턴스 생성 후 호출 

html 요소에 적용하지 않았기 때문에 template요소에는 접근 불가능. 

data와 반응성을 생성하고 주입한 이후이기 때문에, data에 접근하고 method로 로직 실행이 가능

주로 data로 속성을 가져오거나 외부 데이터를 가져와 해당 데이터를 감지하기 위한 리스너를 선언. 

**beforeMount** 

Vue 인스턴스가 마운트되기 직전에 호출 

template 속성에 지정한 html을 render()로 변환 후 el 속성에 지정한 html 요소에

 vue 인스턴스를 연결하기 직전. 

가상DOM이 생성된 상태이기 때문에 실제 DOM에는 접근할 수 없음 

주로 마운트 이전에 필요한 작업을 수행할 때 사용.

 (ex. 외부 라이브러리 연결 설정, 초기화된 데이터로 비동기 작업 수행)

**mounted**

vue 인스턴스가 마운트 되고 나서 호출됨(el 속성에 지정한 화면 요소에 vue 인스턴스가 연결된 직후)

template 속성에 작성된 html 요소에 접근할 수 있어 화면을 제어하는 로직을 수행함. 

모든 요소에 접근 가능(template속성 내 내용이 실제 DOM으로 완성되었기 때문)

속성 변경이나 이벤트리스너 등록 가능 

웹 페이지가 부모와 자식 구조의 컴포넌트로 구성되어있다면, 자식의 mounted가 부모보다 먼저 호출됨

vue의 렌더링은 비동기로 이뤄지기 때문에 두 컴포넌트의 mounted훅은 동시에 발생 x. 

자식 컴포넌트의 mounted에서 $nextTick을 사용해 부모 컴포넌트의 마운트를 완료한 다음 로직 실행가능

**beforeUpdate** 

vue인스턴스가 업데이트되기 직전에 호출. 

데이터의 변화에 따라 화면이 즉각 반응해 갱신함. 

**updated** 

vue인스턴스가 업데이트 되고 나서 호출(변경된 데이터가 DOM에 반영되고 난 이후)

데이터를 변경하고 나서 화면 요소 제어 시 사용

updated 훅 사용 시 화면 갱신에 주의하여야 함. (데이터 변경 시 화면 갱신 → update 무한 루프 주의)

**beforeUnmount**

마운트 해제 전 호출. 

서버 사이드 렌더링 중에 호출하지 x 

호출된 경우에도 컴포넌트 인스턴스는 여전히 작동함. 

인스턴스가 사라지기 전에 해야할 일 처리(이벤트리스너 해제, api 연결 해제, 인스턴스와 관련된 리소스 정리)

**unmounted** 

컴포넌트가 마운트 해제된 후 실행됨 

이 훅을 사용하여 타이머, DOM 이벤트 리스너 또는 서버 연결과 같이 수동으로 생성된 사이드 이펙트를 정리

컴포넌트가 언마운트된 것으로 간주되는 경우 : 

- 모든 자식 컴포넌트가 언마운트
- 모든 반응형 effect가 중지됨


