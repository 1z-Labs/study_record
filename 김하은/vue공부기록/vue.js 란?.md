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
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCiXz0%2FbtqBQ1iMiVT%2FstaXr7UO95opKgXEU01EY0%2Fimg.png" />

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




