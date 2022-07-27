# Step3 - getters, mapGetters

### 정리
- `getters` 내에서 `getters`의 다른 함수를 불러 사용할 수 있다.
- `$store.getters.함수명` 과같이 사용하다보면 `$store.getters`부분이 반복이 되는데  
이를 `mapGetters` 를 통해 축약할 수 있다.

### 사용방법
- `getters` 에서 `getters` 내 다른 함수 사용하기 
  1. 파라미터로 `getters`를 추가한다.
  2. 주의할 점은 `state`를 사용하지 않더라도 `state`까지 표시해줘야한다. 
```javascript
getters: { // computed 의 역할
  allUsersCount: state => {
    return state.allUsers.length
  }, 
  countOfSeoul: state => {
    let count = 0
    state.allUsers.forEach((user) => {
      if (user.address === 'Seoul') count++
    })
    return count
  },
  percentOfSeoul: (state, getters) => { // vuex 에서 내부적으로 파라미터의 순서가 있기 때문에 getters만 사용하더라도 state까지 선언해주어야 한다.
    return Math.round(getters.countOfSeoul / getters.allUsersCount * 100)
  }
}
```
- `mapGetters` 사용하기
   1. 컴포넌트에서 `mapGetters` 를 import 한다.
   2. `...mapGetters(['getters에 선언한 함수명1','getters에 선언한 함수명2'])` 와 같이 사용한다.
   3. `mapGetters`에 선언하면 그 뒤로는 `getters`의 함수를 사용할때 `$store.getters`를 생략해도 된다.
```javascript
import { mapGetters } from 'vuex'

computed: {
...mapGetters(['allUsersCount', 'countOfSeoul', 'percentOfSeoul'])
}
```
