# Step2 - getters

### 정리
- 유저의 수를 구하는 함수를 구현하면 `$store.state.allUsers.length` 로 표현할 수 있다.
- 보통 이런 계산식의 경우 vue의 `computed`를 활용해 관리를 한다.
- vuex의 store에서 `computed` 와 비슷한 기능을 하는것이 `getters`이다.
- `state`속성과 마찬가지로 store 객체 내에 `getters`프로퍼티를 선언하고 `getters` 내에 함수를 선언해두면 모든 컴포넌트에서 해당 함수를 가져다 쓸 수 있다.

### 사용방법
1. 저장소 파일인 store.js에 `getters` 프로퍼티를 선언한다.
2. getters 내에 사용할 함수를 선언한다. `state`에 있는 데이터를 사용하기 위해 함수의 파라미터로 `state`를 선언해 주어야 한다.
```vue
getters: {
  allusersCount: state => state.allUsers.length
}
```
3. 사용하는 곳에서 `$store.getters.allUsersCount` 를 통해 함수를 사용할 수 있다.