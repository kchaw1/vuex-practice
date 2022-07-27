# step1 - state

### 정리
- AllUsers 컴포넌트의 data() 내에 있는 `allusers` 를 store.js 의 state 내로 옮긴다.
- 이제 `allUsers`는 중앙저장소인 store 에서 관리하게 되고 어느 컴포넌트에서든 가져다 사용할 수 있다.
- `$store.state.변수명` 을 통해서 접근 가능하다.