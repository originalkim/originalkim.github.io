---
title: "#[inline] 속성"
description: "#[inline] attribute"
author: ky0422
date: 2022-10-28 21:10:00 +0900
categories: ["C. 프로그래밍", "Rust"]
tags: ["Rust", "러스트", "inline"]
_tistory: https://ky0422.tistory.com/24
archive: true
---

## 개요

일단 `inline` 함수가 무엇인지부터 알아봐야 합니다.

이는 본래 C/C++에서 유래되었는데, C/C++의 `inline`과 상당히 비슷합니다.  
`inline` 함수의 작동 원리를 보기 전에, 일반적인 함수가 어떻게 작동하는지부터 알아봐야 하는데, 일반적으로 함수가 호출되면, 함수가 존재하는 코드로 점프하고, 실행이 끝나면 다시 원래 위치로 돌아옵니다.

여기서 `inline` 함수의 차이점이 들어납니다: `inline` 함수는 함수의 코드를 함수를 호출하는 부분에 복사합니다.  
이는 매크로와 유사해보이는데, `inline` 함수는 개발자 입장에서 일반적인 함수와 똑같습니다만, 내부적으론 다릅니다.

물론 `inline` 함수를 많이 사용하는 것은 오히려 독이 될 수 있습니다: 많은 `inline` 함수를 호출하면, 그 많은 코드가 복사된다는 뜻이고, 이는 곧 느려질 수 있다는 뜻이죠.

그럼 이 `inline` 함수는 언제 써야 할까요? 사실 개발자가 직접 `inline`을 명시해주는 것은 그다지 좋은 선택이 아닙니다.

러스트 컴파일러는 알아서 `inline`을 사용할지 말지 결정합니다.  
이 부분에 대해선 우리보다 컴파일러가 더 똑똑하니, 굳이 명시해줄 필요는 없습니다.

## 그래도 굳이 쓰고싶다면 ...

러스트엔 `inline` 함수를 명시해주는 속성이 있습니다: `#[inline(..)]`

크게 `#[inline]`, `#[inline(always)]` 그리고 `#[inline(never)]`가 존재하는데, 각각 하는 일은 다음과 같습니다:

- `#[inline]`: `inline` 함수가 되어야 함을 명시합니다. 항상 `inline` 되는 것은 아닌데, 이 또한 컴파일러가 결정합니다.
- `#[inline(always)]`: `#[inline]` 보다 더 강력하게 `inline` 함수가 되어야 함을 명시합니다. 물론 항상 `inline` 함수가 되진 않습니다.
- `#[inline(never)]`: `inline` 함수가 되면 안된다는 것을 명시합니다.

이러한 `#[inline]` 속성은 `new`와 같은 함수같은 단순한 함수(또는 Helper 함수)에 주로 사용됩니다:

```rust
struct Foo(u8);

impl Foo {
    #[inline]
    fn new(x: u8) -> Self {
        Foo(x)
    }
}
```
