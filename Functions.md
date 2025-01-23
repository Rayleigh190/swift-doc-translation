# [Functions(함수)](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/)

> 함수를 정의하고 호출하고 argument를 붙이고 반환 값을 사용합니다.

함수는 특정 작업을 수행하는 독립된 코드 덩어리이다. 함수에 해당 함수가 무엇을 하는지 식별할 수 있는 이름을 정의하고, 이 이름은 함수를 호출 하는데 사용된다.

Swift의 unified function syntax는 매개변수 이름이 없는 C 스타일 함수부터 각 매개변수에 이름과 argument label이 있는 복잡한 Objective-C 스타일 메서드까지 표현할 수 있을 만큼 유연하다.

Swift의 모든 함수는 함수의 파라미터 타입과 반환 타입을 가진다. Swift의 모든 타입을 사용할 수 있으며, 함수를 다른 함수의 파라미터로 전달할 수 있고 함수에서 함수를 반환할 수 있다. 중첩된 함수 범위 내에 유용한 기능을 캡슐화하기 위해 다른 함수 내에 함수를 작성할 수도 있다.

## [함수 정의 및 호출](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Defining-and-Calling-Functions)

함수를 정의할 때는 선택적으로 하나 이상의 이름과 타입이 정의된 함수가 입력으로 받는 값을 정의할 수 있다(이걸 파라미터라고 함). 또한 함수가 완료되었을 때 반환할 값의 타입을 정의할 수 있으며 이를 return type이라고 한다.

모든 함수는 함수 이름이 있고, 이는 함수가 수행하는 작업을 설명한다. 함수를 사용하려면 함수 이름으로 호출하고 함수 파라미터 타입과 일치하는 입력 값(arguments)을 전달한다. 함수의 arguments는 반드시 함수의 파라미터 순서와 동일해야 한다.

아래 예시의 함수는 사람의 이름을 입력으로 받아서 그 사람의 인사말을 반환한다. 그래서 greet(person:)이라고 한다. 이 함수를 만들기 위해서는 하나의 입력 파라미터(person이라는 String 값)와 인사말을 포함하는 String 타입의 반환 값을 정의해야 한다:

```swift
func greet(person: String) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
```

이 모든 정보는 func 키워드로 시작하는 함수 정의에 포함된다. 함수의 반환 타입은 '->'로 표시하고, 그 뒤에 반환 타입의 이름을 지정한다.

함수의 정의는 함수가 무엇을 하는지, 무엇을 받을 것으로 기대하는지, 완료 시 무엇을 반환하는지 설명한다. 함수의 정의를 통해 코드 어디에서도 함수를 명확하게 호출하는 것이 쉬워진다:

```swift
print(greet(person: "Anna"))
// Prints "Hello, Anna!"
print(greet(person: "Brian"))
// Prints "Hello, Brian!"
```

greet(person:) 함수는 greet(person: "Anna") 처럼 person argument label 뒤에 String 값을 전달하여 호출한다. 이 함수는 String 값을 반환하므로 greet(person:)을 print(_:separator:terminator:) 함수로 감싸서 해당 문자열을 출력하고 반환 값을 확인할 수 있다.

> __Note__\
> print(_:separator:terminator:)함수에는 첫 번째 argument에 대한 label이 없고, 다른 argument는 기본값이 있으므로 선택사항(optional)이다. 함수 구문(syntax)의 이러한 변형은 아래 [Function Argument Labels and Parameter Names](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions#Function-Argument-Labels-and-Parameter-Names)와 [Default Parameter Values](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions#Default-Parameter-Values)에서 설명한다.

greet(person:) 함수의 body는 greeting이라는 새 String 상수(constant)를 정의하고 간단한 인사말 메시지로 설정하는 것을 시작한다. 그런 다음 이 인사말은 return 키워드를 사용하여 함수 밖으로 전달된다. return greeting이라는 코드에서 함수는 실행을 마치고 greeting의 현재 값을 반환한다.

greet(person:) 함수는 서로 다른 입력 값으로 여러번 호출할 수 있다. 위의 예는 "Anna"의 입력 값과 "Brain"의 입력 값으로 호출되는 경우 어떤 일이 발생하는지 보여준다. 이 함수는 각각의 경우에 맞는 맞춤형 인사말을 반환한다.

이 함수의 body를 더 짧게 만들려면 메세지 생성과 반환 명령문을 한 줄로 결합할 수 있다.

```swift
func greetAgain(person: String) -> String {
    return "Hello again, " + person + "!"
}
print(greetAgain(person: "Anna"))
// Prints "Hello again, Anna!"
```
