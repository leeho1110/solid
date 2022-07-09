# SOLID

링크: https://www.youtube.com/watch?v=HIWJ8sF8lO8&list=PLeQ0NTYUDTmMM71Jn1scbEYdLFHz5ZqFA&index=14
상태: 오늘은 무엇을 할까
유형: 작업 🔨
최종 편집일자: 2022년 7월 9일 오후 11:52
카테고리: OOP

### 개요

SOLID란 무엇이고 왜 필요한 것일까?

---

### The Source Code is the Design

- 소프트웨어 엔지니어는 프로덕트 코드가 아닌 document를 만든다.
    - 집을 짓는 전략과 소프트웨어를 만드는 전략은 다르다.
    - 건축은 설계는 저렴하지만 실제 구현 단계예서 변경은 높은 비용을 유발한다.
    - 하지만 소프트웨어는 구현(컴파일,빌드)는 저렴하지만, 비싼 설계 비용(소스 코드 작성)을 갖는다.

---

### Design Smells

따라서 우린 좋은 설계(소스 코드 작성)을 해야만 한다. 그렇다면 이를 체크하기 위한 기준은 무엇이 있을까?

1. Rigidity
    - 시스템의 강한 의존성때문에 변경하기가 어려워지는 것
    - 원인
        - 많은 시간이 소요되는 테스트와 빌드
        - 의존성 관리를 잘못해서 전체를 리빌드하는 케이스
2. Fragility
    - 모듈의 변화가 다른 모듈에 영향을 끼치는 경우
        - ex. 자동차 라디오의 수정이 창문에 영향을?
    - 컴파일 타임 의존성은 다형성 디스패치를 통해 해결할 수 있다.
3. Immobility
    - 모듈을 추출해서 재사용하는 작업이 쉽지 않는 경우
    - 특정 UI, 특정 DB에 강하게 결합되어 있다면 재사용이 어렵다
    - 결합도를 없애야 한다.
4. Viscosity
    - 체크인, 체크아웃, 머지 등이 비용이 크고 어렵다면 viscosity가 높다.
    - 시스템이 너무 무겁고 여러 레이어를 가로질러 의존성을 갖는 일들이 예시다.
    - Irresponsible tolerance(무책임한 용인)
        - 코드를 작성하는 개발자도 이것이 잘못된 것인지 안다. 하지만 여러 요인에 의해 넘어간다.
        - 결국은 누군가 그 똥을 밟게 되어있다.
    - 이것 역시 컴파일 타임 의존성과 런타임 의존성을 인터페이스로 해결할 수 있다.

---

### Procedural & OOP

- Procedural
    - 장치가 증가하면 Fan-out
    - 상위 모듈이 하위 모듈을 의존하고 있다. 상위 모듈에서 하위 모듈로 의존성이 흐른다.
- OOP
    - 의존성의 역전이 일어난다. IoC
    - 런타임 의존성은 상위 모듈에서 하위 모듈로 가는게 맞지만, 컴파일 타임에서는 인터페이스를 통해 하위 레벨에서 상위 레벨로 갈 수 있도록 의존성이 역전되어야 한다.
    - Dynamic polymorphism
        - OO는 메시지를 전달하는 것이다.
        - 어떻게 세부적으로 동작하는지는 모르고, 무엇을 원하는지를 전달하는 것
    - 즉 Dependeny Inversion이 핵심이다.
        - 캡슐화, 추상화, 상속은 객체지향의 ‘메커니즘’이다.
    - IoC를 통해 상위 레벨의 모듈을 하위 레벨의 모듈로부터 보호하는 것이 OO의 핵심이다.
    - 객체지향 디자인은 의존성을 잘 관리하는 것이다.
        - 이것을 잘 관리하기 위해 필요한 규칙이 SOLID다.

---

### *Ref*

- [https://youtu.be/HIWJ8sF8lO8](https://youtu.be/HIWJ8sF8lO8)
- [https://howtodoinjava.com/best-practices/solid-principles/](https://howtodoinjava.com/best-practices/solid-principles/)