# Truthy and Falsy

예를 들어 다음과 같은 함수가 있다고 가정해봅시다

![1](https://user-images.githubusercontent.com/67893516/100458205-b9b2ce00-3106-11eb-8c47-dfa740f9d97c.png)

이 상황에서 만약 print 함수가 아래 사진과 같이 파라미터가 비어진 상태로 실행되었다고 가정해봅시다

![2](https://user-images.githubusercontent.com/67893516/100458210-bae3fb00-3106-11eb-8cd6-80a01b51c4ca.png)

그러면 다음과 같은 에러가 발생하게 됩니다

```jsx
TypeError: Cannot read property 'name' of undefined
```

이러한 상황에서, 만약에 print 함수에서 만약에 object 가 주어지지 않았다면,
문제가 있다고 콘솔에 출력해야 한다면 아래와 같이 구현 할 수 있습니다.

![3](https://user-images.githubusercontent.com/67893516/100458219-bc152800-3106-11eb-8e9c-5b90802880f8.png)

그런데 만약에 다음과 같이 print 에 null 값이 파라미터로 전달되면 어떨까요?

![4](https://user-images.githubusercontent.com/67893516/100458224-bd465500-3106-11eb-8adb-c619e9a4ccf0.png)


그러면 또 오류가 발생하게 됩니다

```jsx
TypeError: Cannot read property 'name' of null

```

그렇다면 또 null일때의 조건을 코드에 추가해줘야 합니다

![5](https://user-images.githubusercontent.com/67893516/100458228-bfa8af00-3106-11eb-9f2d-5754596140df.png)

이렇게 person 이 undefined 이거나, null 인 상황을 대비하려면 위와 같이 코드를 작성해야하는데요, 여기서 위 코드는 다음과 같이 축약해서 작성 할 수 있습니다

![6](https://user-images.githubusercontent.com/67893516/100458232-c0414580-3106-11eb-9325-42c00de8bc69.png)

이게 작동하는 이유는, undefined 와 null 은 Falsy 한 값입니다.
Falsy 한 값 앞에 느낌표를 붙여주면 true 로 전환됩니다.

```jsx
console.log(!undefined);
console.log(!null);

```

undefined와 null은 falsy 값입니다

Falsy 한 값은 이 외에도 몇개 더 있습니다.

```jsx
console.log(!undefined);
console.log(!null);
console.log(!0);
console.log(!'');
console.log(!NaN);

```

위 값들은 true가 됩니다

위 값 이외의 값들은 모두 트루가 됩니다

```jsx
console.log(!3);
console.log(!'hello');
console.log(!['array?']);
console.log(![]);
console.log(!{ value: 1 });

```

아까와 반대로 위 값들은 모두 false가 됩니다.

Truthy 한 값과 Falsy 한 값은 if 문에서도 사용 할 수있습니다.

```jsx
const value = { a: 1 };
if (value) {
  console.log('value 가 Truthy 하네요.');
}

```

value 가 Truthy 한 값이기 때문에, 콘솔에 메시지가 출력 될 것입니다.

반면, value 가 null, undefined, 0, '', NaN 중 하나라면, 나타나지 않을 겁니다.

그래서 이렇게, Truthy 한 값과 Falsy 한 값을 잘 알아놓으면 조건문을 작성할 때 편할 것입니다.

추가적으로, 알아두면 유용한 팁 하나를 드리겠습니다.

만약에, 특정 값이 Truthy 한 값이라면 true, 그렇지 않다면 false 로 값을 표현하는 것을 구현해보겠습니다.

```jsx
const value = { a: 1 };

const truthy = value ? true : false;

```

우리가 이전에 배운 삼항연산자를 사용하면 쉽게 value 값의 존재 유무에 따라 쉽게 true 및 false 로 전환이 가능합니다. 그런데, 이를 더 쉽게 할 수도 있습니다.

```jsx
const value = { a: 1 };
const truthy = !!value;

```

!value 는 false 가 되고, 여기에 !false 는 true 가 되어서, 결과는 true 가 됩니다.