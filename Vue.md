# Vue.js
### 뷰 인스턴스
- 뷰 인스턴스 형식 
```html
new Vue ({
    ...
})
```
- 뷰 인스턴스 속성 
    - el : vue로 만든 화면이 그려지는 시작점을 의미한다. 뷰 인스턴스로 화면을 렌더링할때 화면이 그려질 위치의 돔 요소를 지정해주어야한다. # 선택자는 css선택자 규칙과 같다.
    <details>
    <summary>css선택자 규칙</summary>  
    <div markdown="1">
    #id이름 : id값을 선택하는 셀렉터이다.
    모든 속성은 숫자, 대문자, 특수문자로 시작할 수 없으며 영문소문자로 작성한다.
    단어의 구분을 위하여 하이픈 표기법을 사용한다
    마지막 속성 값의 끝에도 세미콜론을 사용한다.
    </div>
    </details>
    - data : 뷰 인스턴스의 데이터 객체로 객체 또는 함수의 형태로 작성할수있다. 컴포넌트를 정의할 때 data는 데이터를 반환하는 함수로 선언해야한다. 화살표함수를 사용할 수 없다.
    <details>
    <summary>화살표함수의 제한점</summary>  
    <div markdown="1">
    - this가 없다. 화살표함수 본문에서 this에 접근하면 외부에서 값을 가져온다.
    - this가 없기 때문에 화살표함수는 생성자 함수로 사용할 수 없다. new와 함께 호출할 수 없다.
    </div>
    </details>
    - methods : 화면 로직제어와 관계된 메서드를 정의하는 속성, 마우스 클릭 이벤트 처리와 같이 화면의 전반적인 이벤트와 화면 동작과 관련된 로직을 추가할수 있다. 모든 메소드는 자동으로 this 컨텍스트를 뷰 인스턴스에 바인딩
    - tmplate : 화면에 표시할 HTML, CSS등의 마크업 요소를 정의하는 속성, 뷰의 데이터 및 기타 속성들도 함께 화면에 그릴 수 있다. template은 연결된 엘리먼트를 대체한다. 뷰 옵션에 render함수가 있으면 템플릿속성은 무시된다.
- 데이터 바인딩
    - {{}} 콧수염 괄호 : 뷰 인스턴스의 데이터를 HTML 태그에 연결하는 가장 기본적인 텍스트 삽입방식이다.
    ```HTML
    <div id="app">
      <h2>{{ msg }}</h2>
      <h2 v-once>{{ msg }}</h2>
    </div>

    <script>
      const app = new Vue({
        el: '#app',
        data() {
          return {
            msg: '오늘 점심 류산슬덮밥',
          };
        },
      });
    </script>
    ```
    data 속성의 msg값이 바뀌면 뷰 반응성에 의해 화면이 자동으로 갱신된다. 
    뷰 데이터가 변경되어도 값을 바꾸고 싶지 않다면 `v-once` 속성을 사용한다.(일회성 보간)
    - v-bind : 아이디, 클래스, 스타일 등의 HTML속성(attributes)값에 뷰데이터 값을 연결할 때 사용되는 데이터 연결 방식이다. `v-bind:id` === `:id`
- 자바스크립트 표현식 : {{}}안에 자바스크립트 표현식을 넣어서 사용할 수 있다.
    - 자바스크립트의 선언문과 분기 구문(if,switch)은 사용할 수 없다. 삼항연산자 사용.
    - 복잡한 연산은 인스턴스 안에서 처리하고 화면에는 간단한 연산 결과만 표시해야한다. 
- 뷰 디렉티브 : HTML 태그 안에 v- 접두사를 가지는 속성
    - v-if : 지정한 뷰데이터 값의 참거짓 여부에 따라 해당 태그를 화면에 표시하거나 표시하지 않는다.
    - v-for : 지정한 뷰데이터의 개수만큼 해당 태그를 반복출력한다. 현재 엘리먼트에 대한 별칭, 인덱스의 별칭을 사용할 수 있다. 기본적으로 엘리먼트를 이동하지 않고 그 자리에서 패치 시도한다. 강제로 엘리먼트의 순서를 바꾸려면 특수속성 key를 설정해야한다.
    - v-if와 함께 사용하는 경우 v-for는 v-if보다 높은 우선순위를 갖는다. 
    - v-show :  v-if와 유사하게 데이터의 진위 여부에 따라 해당 태그를 화면에 표시하거나 표시하지않는다. **v-if는 해당 태그를 완전히 삭제하지만 v-show는 css효과만 display:none으로 주어 실제 태그는 남아있고 화면 상으로만 보이지 않는다.**
    - v-on : 화면 요소의 이벤트를 감지하여 처리할 때 사용한다. v-on:click은 해당 태그의 클릭 이벤트를 감지하여 특정 메서드를 실행할 수 있다. `v-on:click === @click` 엘리먼트에 이벤트리스너를 연결하고 이벤트 유형은 전달인자로 표시한다.
    - v-cloak : 뷰 인스턴스가 준비될때까지 콧수염바인딩을 숨기는 데 사용한다. 
- computed : 데이터를 가공하는 등 복잡한 연산은 뷰 인스턴스 안에서 하고 최종적으로 HTML에는 데이터를 표현해야한다. computed 속성은 이러한 데이터 연산들을 정의하는 영역이다.
    - data 속성 값의 변화에 따라 자동으로 다시 연산한다는 점이다. compited속성에서 사용하고 있는 data 값이 변경되면 전체 값을 다시 한번 계산한다.
    - 캐싱이 가능하다. 캐싱은 동일한 연산을 반복해서 하지 않기 위해 연산의 결과 값을 미리 저장하고 있다가 필요할 때 불러오는 동작이다. 
    - computed 속성과 methods 속성의 차이점 : methods속성은 호출할 때만 해당 로직이 수행되고, computed 속성은 대상 데이터의 값이 변경되면 자동적으로 수행된다는 것이다. 다시말해 수동적으로 데이터를 갱신하느냐, 능동적으로 갱신하느냐의 차이다.
    - Getter와 Setter를 직접 지정할 수 있다. 작성은 method 형태로 정의하지만 Vue에서 프록시처리하여 property처럼 사용한다.
- Vue watch : 데이터 변화를 감지하여 자동으로 특정 로직을 수행한다. computed와 유사하지만 computed는 내장 API를 활용한 간단한 연산 정도로 적합한 반면, watch 속성은 데이터 호출과 같이 상대적으로 더 많이 소모되는 비동기처리에 적합하다.