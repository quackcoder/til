# 2장 의미있는 이름

### 의도를 분명히 밝혀라

- 의도가 분명한 이름이 **정말로 중요**하다.

  ```java
  // Bad
  int d; // 경과 시간(단위: 날짜)


  // Good
  int elapsedTimeInDays;
  int daysSinceCreation;
  int daysSinceModification;
  int fileAgeInDays;
  ```

### 그릇된 정보를 피하라

- 프로그래머는 코드에 그릇된 단서를 남겨서는 안 된다. 그릇된 단서는 코드 의미를 흐린다.
- 서로 흡사한 이름을 사용하지 않도록 주의한다.
- 그러나 유사한 개념은 유사한 표기법을 사용한다. 일관성이 떨어지는 표기법은 그릇된 정보다.

### 의미 있게 구분하라

- 불용어(noise word)를 추가하는 방식은 적절하지 못하다.

  ```java
  // Bad
  public static void copyChars(char a1[], char a2[]) {
      for (int i = 0; i < a1.length; i++) {
          a2[i] = a1[i];
      }
  }

  // Good
  public static void copyChars(char source[], char destination[]) {
      for (int i = 0; i < a1.length; i++) {
          destination[i] = source[i];
      }
  }
  ```

- `customerInfo`는 `customer`와, `accountData`는 `account`와, `theMessage`는 `message`와 구분이 안 된다. 읽는 사람이 차이를 알도록 이름을 지어라.

### 발음하기 쉬운 이름을 사용하라

### 검색하기 쉬운 이름을 사용하다

### 인코딩을 피하라

#### 헝가리식 표기법

변수나 함수의 이름에 그 종류, 곧 흔히 데이터 타입 따위를 명시하는 표기법으로, 명명규칙의 일종이다. ([위키백과](https://ko.wikipedia.org/wiki/%ED%97%9D%EA%B0%80%EB%A6%AC%EC%95%88_%ED%91%9C%EA%B8%B0%EB%B2%95))

```java
PhoneNumber phoneString;
```

#### 멤버 변수 접두어

```java
// Bad
public class Part {
    private String m_dsc;
    void setName(String name) {
        m_dsc = name;
    }
}

// Good
public class Part {
    String description;
    void setDescription(String description) {
        this.description = description;
    }
}
```

#### 인터페이스 클래스와 구현 클래스

    ```java
    IShapeFactory   // 인터페이스 클래스
    ShapeFactory    // 구현 클래스
    ```

    옛날 코드에서 많이 사용하는 접두어 `I`는 (잘해봤자) 주의를 흐트리고 (나쁘게는) 과도한 정보를 제공한다. 차라리 `ShapeFactoryImp`가 좋다.

### 자신의 기억력을 자랑하지 마라

- 전문가 프로그래머는 **명료함이 최고**라는 사실을 이해한다.

### 클래스 이름

- 클래스 이름과 객체 이름은 **명사**나 **명사구**가 적합하다.

### 메서드 이름

- 메서드 이름은 **동사**나 **동사구**가 적합하다.  
  ex. `postPayment`, `deletePage`, `save` 등
- 접근자(Accessor), 변경자(Mutator), 조건자(Predicate)는 javabean 표준에 따라 값 앖에 `get`, `set`, `is`를 붙인다.
  ```java
  string name = employee.getName();
  customer.setName("mike");
  if (paycheck.isPosted()) ...
  ```

### 기발한 이름은 피하라

- 특정 문화에서만 사용하는 농담은 피하는 편이 좋다. 의도를 분명하고 솔직하게 표현하라.

### 한 개념에 한 단어를 사용하라

- 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다. 예를 들어, 똑같은 메서드를 클래스마다 `fetch`, `retrieve`, `get`으로 제각각 부르면 혼란스럽다.

### 말장난을 하지 마라

- 한 단어를 두 가지 목적으로 사용하지 마라. 다른 개념에 같은 단어를 사용한다면 그것은 말장난에 불과하다.
- 여러 클래스에 `add`라는 메서드가 생겼다. 모든 메서드의 매개변수와 반환값이 의미적으로 똑같다면 문제가 없다. 하지만 때로는 프로그래머가 같은 맥락이 아닌데도 **일관성**을 고려해 `add`라는 단어를 선택한다.
  <br/>
  <br/>
  예를 들어, 지금까지 구현한 `add` 메서드는 모두가 기존 값 두 개를 더하거나 이어서 새로운 값을 만든다고 가정하자. 새로 작성하는 메서드는 집합에 값 하나를 추가한다. 이 메서드를 `add`라 불러도 괜찮을까? <u>새 메서드는 기존 `add` 메서드와 맥락이 다르다.</u> 그러므로 `insert`나 `append`라는 이름이 적당하다.

### 해법 영역에서 가져온 이름을 사용하라

- 코드를 읽는 사람도 프로그래머라는 사실을 명심한다. 그러므로 전산 용어, 알고리즘 이름, 패턴 이름, 수학 용어 등을 사용해도 괜찮다.
- 기술 개념에는 기술 이름이 가장 적합한 선택이다.

### 문제 영역에서 가져온 이름을 사용하라

- 적절한 '프로그래머 용어'가 없다면 문제 영역에서 이름을 가져온다.
- 우수한 프로그래머와 설계자라면 해법 영역과 문제 영역을 구분할 줄 알아야 한다.

### 의미 있는 맥락을 추가하라

### 불필요한 맥락을 없애라
