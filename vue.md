## Vue 

- disappear div below certain screen width
  ```css
  @media screen and (max-width: 1400px){
    #container {
      display: none;
    }
  }
  ```

- EventBus
  ```vue
  // 이벤트버스 생성
  var EventBus = new Vue()
  // 이벤트 발행
  EventBus.$emit('message', 'hello world');
  // 이벤트 구독
  EventBus.$on('message', function(text) {
      console.log(text);
  });
  ```
