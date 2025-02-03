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
- 선언하려는 엔터티의 요약으로 시작하라. API 선언과 요약만으로도 완전히 이해될 때가 있다.
```swift
/// Returns a "view" of `self` containing the same elements in
/// reverse order.
func reversed() -> ReverseCollection
```