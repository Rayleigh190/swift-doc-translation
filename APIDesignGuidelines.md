# [API 디자인 가이드라인](https://www.swift.org/documentation/api-design-guidelines/)

## [목차](https://www.swift.org/documentation/api-design-guidelines/#table-of-contents)
- Introduction(소개)
- Fundamentals(기본사항)
- Naming(이름짓기)
  - Promote Clear Usage
  - Strive for Fluent Usage
  - Use Terminology Well
- Conventions
  - General Conventions
  - Parameters
  - Argument Labels
- Special Instructions

## Introduction(소개)
Swift 코드를 작성할 때 명확하고 일관된 개발자 경험은 주로 API에 나타나는 이름관 관용어로부터 온다. 이런 디자인 가이드라인은 당신의 코드가 Swift 생태계의 이불처럼 느껴지도록 한다.

## Fundamentals(기본사항)
- **사용 시점에 명확한 것**이 가장 중요하다. 메서드와 프로퍼티와 같은 엔터티는 한 번만 선언되지만 반복적으로 사용된다. 용도가 명확하고 간결하도록 API를 설계해야한다. 디자인을 평가할 때 선언문을 읽는 것만으로 충분하지 않다. 항상 사용할 때 맥락상 명확하게 보이는지 확인해야 한다.
- **간결함보다 명확함이 더 중요하다.** Swift 코드는 충분히 간결해질 수 있지만, 가장 적은 문자로 가장 작은 코드를 만드는 것이 목표가 아니다. Swift 코드에서 간결성은 강한 타입 시스템과 자연스럽게 반복적으로 재사용하는 코드(boilerplate)를 줄이는 기능의 부작용이다.
- 모든 선언에 대해 **문서 주석을 작성**하라. 문서를 작성하며 얻은 통찰력은 디자인에 큰 영향을 미출 수 있으니 미루지 말자.
> API를 간단히 설명하는게 어렵다면, API를 잘못 설계했을 지도 모른다.

### 자세한 내용
- Swift의 [마크다운 문법](https://developer.apple.com/library/archive/documentation/Xcode/Reference/xcode_markup_formatting_ref/)을 사용하라.
- 선언하려는 엔터티의 **요약으로 시작하라**. API 선언과 요약만으로도 완전히 이해될 때가 있다.
```swift
/// Returns a "view" of `self` containing the same elements in
/// reverse order.
func reversed() -> ReverseCollection
```
<details>
<summary>더 자세히 보기</summary>

- **요약에 집중**하는 것이 가장 중요하다. 많은 훌륭한 문서의 주석은 훌륭한 요약에 불과하다.
- 가능한 완전한 문장이 아닌 마침표로 끝나는 **단일 문장**을 사용하라.
- null 효과와 Void 반환을 제외하고 **함수 또는 메서드의 기능과 반환 내용을 설명하라**:
```swift
/// Inserts `newHead` at the beginning of `self`.
mutating func prepend(_ newHead: Int)

/// Returns a `List` containing `head` followed by the elements
/// of `self`.
func prepending(_ head: Element) -> List

/// Removes and returns the first element of `self` if non-empty;
/// returns `nil` otherwise.
mutating func popFirst() -> Element?
```
참고: 위의 `popFirst`와 같이 세미콜론으로 여러 문장이 조각으로 구성 될 수 있다.
- **구독자가 액세스하는 내용을 설명하라:**
```swift
/// Accesses the `index`th element.
subscript(index: Int) -> Element { get set }
```
- **초기화로 무엇이 생성되는지 설명하라:**
```swift
/// Creates an instance containing `n` repetitions of `x`.
init(count n: Int, repeatedElement x: Element)
```
- 모든 선언에 대해서, **선언된 엔터가 무엇인지 설명하라.**
```swift
/// A collection that supports equally efficient insertion/removal
/// at any position.
struct List {

  /// The element at the beginning of `self`, or `nil` if self is
  /// empty.
  var first: Element?
  ...
```

</details>