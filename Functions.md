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

이 함수의 body를 더 짧게 만들려면 메세지 생성과 반환 명령문을 한 줄로 결합할 수 있다:

```swift
func greetAgain(person: String) -> String {
    return "Hello again, " + person + "!"
}
print(greetAgain(person: "Anna"))
// Prints "Hello again, Anna!"
```
## [함수 파라미터 및 반환 값](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Function-Parameters-and-Return-Values)

Swift에서 함수의 파라미터와 반환 값은 매우 유연하다. 이름 없는 단일 파라미터를 갖는 간단한 utility 함수부터 파라미터 이름과 다양한 파라미터 옵션을 갖는 복잡한 함수까지 무엇이든 정의할 수 있다.

### [파라미터 없는 함수](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Functions-Without-Parameters)

함수는 꼭 입력 파라미터를 정의할 필요가 없다. 다음은 입력 파라미터가 없는 함수로, 호출될 때마다 항상 동일한 String 메시지를 반환한다:

```swift
func sayHelloWorld() -> String {
    return "hello, world"
}
print(sayHelloWorld())
// Prints "hello, world"
```

함수를 정의할 때는 파라미터가 없더라도 함수 이름 뒤에 괄호를 붙여야 한다. 함수가 호출될 때에는 함수 이름 뒤에 빈 괄호 쌍이 따라온다.

### [여러 파라미터가 있는 함수](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Functions-With-Multiple-Parameters)

함수는 여러 개의 입력 파라미터를 가질 수 있으며, 이는 함수의 괄호 안에 쉼표로 구분하여 작성한다.

아래 함수는 사람의 이름과 이미 인사를 받았는지 여부를 입력으로 받고 해당 사람에게 적합한 인사를 반환한다:

```swift
func greet(person: String, alreadyGreeted: Bool) -> String {
    if alreadyGreeted {
        return greetAgain(person: person)
    } else {
        return greet(person: person)
    }
}
print(greet(person: "Tim", alreadyGreeted: true))
// Prints "Hello again, Tim!"
```

greet(person:alreadyGreeted:) 함수는 String 아규먼트 값인 person과 Bool 아규먼트 값인 alreadyGreeted를 괄호로 묶고 쉼표로 구분하여 전달하고 호출한다. 위 함수는 이전 섹션에서 보여준 greet(person:) 함수와 다르다는 것을 유의하자. 두 함수 모두 greet라는 이름을 가지고 있지만 greet(person:alreadyGreeted:) 함수는 두 개의 아규먼트를 받는 반면 greet(person:) 함수는 하나만 받는다.

### [반환 값이 없는 함수](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Functions-Without-Return-Values)

함수는 꼭 반환 타입을 정의할 필요가 없다. 다음은 반환하는 대신 String 값을 출력하는 greet(person:) 함수이다:

```swift
func greet(person: String) {
    print("Hello, \(person)!")
}
greet(person: "Dave")
// Prints "Hello, Dave!"
```

> __Note__\
> 엄밀히 말해서 위 greet(person:) 함수의 반환 값이 정의되어 있지 않더라도 여전히 값을 반환한다. 반환 타입이 정의되지 않은 함수는 자동으로 Void 타입을 반환한다. 이는 단순히 ()로 작성된 빈 튜플이다.

함수의 반환 값은 호출될 때 무시될 수 있다:

```swift
func printAndCount(string: String) -> Int {
    print(string)
    return string.count
}
func printWithoutCounting(string: String) {
    let _ = printAndCount(string: string)
}
printAndCount(string: "hello, world")
// prints "hello, world" and returns a value of 12
printWithoutCounting(string: "hello, world")
// prints "hello, world" but doesn't return a value
```

첫 번째 함수인 printAndCount(string:)은 문자열을 출력한 후 해당 문자열의 문자 수를 Int로 반환한다. 두 번째 함수인 printWithoutCounting(string:)은 첫 번째 함수를 호출하지만 반환 값은 무시한다. 두 번째 함수가 호출되면 메시지는 여전히 첫 번째 함수에 의해 출력되지만 반환 값은 사용되지 않는다.

> __Note__\
> 반환 값은 무시될 수 있지만, 값을 반환한다고 정의한 함수는 항상 반환 값을 반환해야 한다. 반환 타입이 정의된 함수는 값을 반환하지 않고 함수 하단에서 제어로부터 벗어나는 것을 허용할 수 없으며, 그렇게 시도하면 컴파일 타임 오류가 발생한다.

### [여러 반환 값을 갖는 함수](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Functions-with-Multiple-Return-Values)

함수의 반환 타입으로 튜플 타입을 사용하면 여러 값을 하나의 값으로 묶어 반환할 수 있다.

아래의 예제에서는 Int 값의 배열에서 가장 작은 숫자와 가장 큰 숫자를 찾는 minMax(array:)라는 함수를 정의한다.

```swift
func minMax(array: [Int]) -> (min: Int, max: Int) {
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
```

minMax(array:) 함수는 두 개의 Int 값을 가진 튜플을 반환한다. 반환 값은 min과 max라는 label이 지정되어 있으므로 함수의 반환 값에서 이름으로 접근할 수 있다.

minMax(array:) 함수의 body는 currentMin과 currentMax라는 두 개의 변수를 배열의 첫 번째 값(정수)으로 설정하는 것으로 시작한다. 그런 다음 함수는 배열의 첫 번째를 제외한 나머지 값을 반복하고 각 값이 currentMin과 currentMax 값보다 작거나 큰지 확인한다. 결과적으로 두 개의 최대 최소 Int 값이  튜플로 반환된다.

반환 값이 튜플이므로 dot syntax로 접근하여 최대 최소 값을 찾을 수 있다:

```swift
let bounds = minMax(array: [8, -6, 2, 109, 3, 71])
print("min is \(bounds.min) and max is \(bounds.max)")
// Prints "min is -6 and max is 109"
```

### [옵셔널 튜플 반환 타입](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Optional-Tuple-Return-Types)

함수에서 반환되는 튜플 타입이 "no value"일 가능성이 있는 경우 반환 타입을 optional tuple을 사용하여 반환 값이 nil일 수 있다는 것을 반영할 수 있다. 튜플 타입의 닫는 괄호 뒤에 물음표를 붙여 optional tuple 타입을 명시한다. (ex: (Int, Int)? 또는 (String, Int, Bool)?).

> __Note__\
> (Int, Int)?와 같은 optional tuple 타입은 (Int?, Int?)와 같이 내부에 optional tuple 타입을 가지고 있는 튜플과 다르다. optional tuple 타입을 사용하면 튜플 전체가 옵셔널이고 각 개별 값은 아니다.

위의 minMax(array:) 함수는 두 개의 Int 값을 가지는 튜플을 반환한다. 하지만 이 함수는 전달 받은 배열에 대해 어떠한 safety checks를 하지 않는다. 빈 배열일 경우 minMax(array:) 함수는 array[0]에 접근 할 때 런타입 오류를 발생시킨다.

빈 배열을 안전하게 처리하려면 함수의 반환 타입을 optional tuple로 지정하고 배열이 비어 있을 경우 nil 값을 반환한다:

```swift
func minMax(array: [Int]) -> (min: Int, max: Int)? {
    if array.isEmpty { return nil }
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
```
optional binding을 사용하여 위 함수가 실제 튜플 값이나 nil을 반환하는지 확인할 수 있다:

```swift
if let bounds = minMax(array: [8, -6, 2, 109, 3, 71]) {
    print("min is \(bounds.min) and max is \(bounds.max)")
}
// Prints "min is -6 and max is 109"
```

### [Implict Return이 있는 함수](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions/#Functions-With-an-Implicit-Return)

함수 body 전체가 단일 표현식인 경우, 함수는 명시적으로 해당 표현식을 반환한다. 예를 들어, 아래 두 함수는 동일하게 동작한다:

```swift
func greeting(for person: String) -> String {
    "Hello, " + person + "!"
}
print(greeting(for: "Dave"))
// Prints "Hello, Dave!"


func anotherGreeting(for person: String) -> String {
    return "Hello, " + person + "!"
}
print(anotherGreeting(for: "Dave"))
// Prints "Hello, Dave!"
```

`greeting(for:)` 함수는 결국 인사말 메시지이고, 이렇게 함수를 짧게 작성할 수 있다. `anotherGreeting(for:)`도 마찬가지이다. 반환 명령 줄이 한 줄이면 반환 명령 부분을 생략할 수 있다.

[Shorthand Getter Declaration](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/properties#Shorthand-Getter-Declaration)에서도 볼 수 있듯이 property getters는 암묵적 반환을 사용할 수도 있다.

> __Note__\
> 암묵적 반환 값으로 작성한 코드는 어떤 값을 반환해야 한다. 예를 들어, `print(13)`을 암묵적 반환 값으로 사용할 수 없다. 하지만 `fatalError("Oh no!")`와 같이 결코 반환하지 않는 함수를 암묵적 반환 값으로 사용할 수 있다. 이는 Swift가 암묵적 반환이 발생하지 않는다는 것을 알고 있기 때문이다.

