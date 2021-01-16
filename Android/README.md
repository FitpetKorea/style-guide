- FitPet Android 스타일 가이드입니다. 구성원들의 의사결정에 따라 수시로 변경될 수 있습니다.
- 해당 내용 중 Kotlin lint 규칙과 맞지 않는 부분이 있을 경우 Kotlin lint 규칙을 우선하여 변경하도록 합니다.

## 목차
- [코드 레이아웃](#코드-레이아웃)
- [들여쓰기 및 띄어쓰기](#들여쓰기-및-띄어쓰기)
- [줄바꿈](#줄바꿈)
- [최대 줄 길이](#최대-줄-길이)
- [빈 줄](#빈-줄)
- [임포트](#임포트)
- [네이밍](#네이밍)
- [클래스](#클래스)
- [함수](#함수)
- [변수](#변수)
- [상수](#상수)
- [약어](#약어)
- [주석](#주석)
- [프로그래밍 권장사항](#프로그래밍-권장사항)

## 코드 레이아웃
### 들여쓰기 및 띄어쓰기
- 들여쓰기에는 탭(tab) 을 사용합니다.
- 콜론(`:`)을 쓸 때에는 콜론의 오른쪽에만 공백을 둡니다.
```kotlin
var names: String?
```
- 연산자 오버로딩 함수 정의에서는 연산자와 괄호 사이에 한 칸 띄어씁니다.
```kotlin
fun ** (lhs: Int, rhs: Int)
```

### 줄바꿈
- 함수 정의가 최대 길이를 초과하는 경우에는 아래와 같이 줄바꿈합니다.
```kotlin
fun recyclerView(view: RecyclerView, 
selectedIndexPath: Int): RecyclerItemView {​​​​​​​
// doSomething()
}​​​​​​​
```
- 함수를 호출하는 코드가 최대 길이를 초과하는 경우에는 파라미터 이름을 기준으로 줄바꿈합니다.
```kotlin
val actionSheet = ActionSheet( title: "정말 계정을 삭제하실 건가요?", activity: this,
cancelButtonTitle: "취소", destructiveButtonTitle: "삭제해주세요")
```

### 최대 줄 길이
- 한 줄은 최대 99자를 넘지 않아야 합니다.

### 빈 줄
- 빈 줄에는 공백이 포함되지 않도록 합니다.
- 모든 파일은 빈 줄로 끝나도록 합니다.
- 주석 위와 아래에는 공백이 필요합니다.
```kotlin
// Layout
override fun onLayout() {​​​​​​​
// doSomething()
}​​​​​​​
// fragmnet Start
override fun onStart() {​​​​​​​
// doSomething()
}​​​​​​​
```

### 임포트
모듈 임포트는 알파벳 순으로 정렬합니다. 내장 프레임워크를 먼저 임포트하고, 빈 줄로 구분하여 서드파티 프레임워크를 임포트합니다.
```kotlin
import android.animation.Animator
import com.google.firebase.analytics
import dagger.hilt.android
import org.json.JSONException
import timber.log.Timber
```

## 네이밍

### 클래스
- 클래스 이름에는 UpperCamelCase를 사용합니다.
- 클래스 이름에는 접두사<sup>Prefix</sup>를 붙이지 않습니다.

### 함수
- 함수 이름에는 lowerCamelCase를 사용합니다.
- 함수 이름 앞에는 되도록이면 `get`을 붙이지 않습니다.
**좋은 예:**
```kotlin
fun name(for user: User): String?
```
**나쁜 예:**
```kotlin
fun getName(for user: User): String?
```

### 변수
- 변수 이름에는 lowerCamelCase를 사용합니다.

### 상수
- 상수 이름에는 알파벳 대문자와 _를 사용합니다.
**예:**
```kotlin
val MAX_LINES = 3
```

### 열거형
- enum의 각 case에는 알파벳 대문자와 _를 사용한다.
**좋은 예:**
```kotlin
enum class ErrorCode {
	NONE = -1,
	OK = 0,
	INVALID_IMAGE_SIZE = 100,
	INVALID_CHANNEL = 101,  // local test only
	INVALID_TYPE = 301,
}​​​​​​​
```

### 약어
- 약어로 시작하는 경우 소문자로 표기하고, 그 외의 경우에는 항상 대문자로 표기합니다.
**좋은 예:**
<pre>
var ID: Int?
var html: String?
var URL: URL?
var url: String?
</pre>
**나쁜 예:**
<pre>
var Id: Int?
var HTML: String?
var Uri: URL?
var URL: String?
</pre>

## 주석
- 해당 클래스에 대한 설명은 `/*** ***/`를 사용해서 주석을 남깁니다.
- 개별 변수, 함수에 대한 설명은 '//' 를 사용해서 주석을 남깁니다.
```kotlin
/**
 * 사용자 프로필을 그려주는 뷰
 **/ 
class MainActivity: Activity {​​​​​​​

// 사용자 닉네임을 그려주는 텍스트 뷰
var nameTextView: TextView!
}​​​​​​​
```

## 프로그래밍 권장사항
- 가능하다면 변수를 정의할 때 함께 초기화하도록 합니다. 
apply 을 사용하면 초기화와 함께 속성을 지정할 수 있습니다.
```kotlin
val label = TextView(context).apply {​​​​​​​
  textColor = .black
  text = "Hello, World!"
}​​​​​​​
```
- 상수를 정의할 때에는 `enum`를 만들어 비슷한 상수끼리 모아둡니다. 재사용성과 유지보수 측면에서 큰 향상을 가져옵니다. `struct` 대신 `enum`을 사용하는 이유는, 생성자가 제공되지 않는 자료형을 사용하기 위해서입니다. 
```kotlin
class ProfileActivity: Activity {​​​​​​​
  enum InspectionType(val value: String) {​​​​​​​
    AHEAD("Ahead"),
    BALANCE("Balance"),
    GENE("Gene")
  }​​​​​​​
  enum Color(val colorValue: Int) {​​​​​​​
    RED(getColor(R.color.red)),
    BLUE(getColor(R.color.blue)
  }​​​​​​​
}​​​​​​​
```   
이렇게 선언된 상수들은 다음과 같이 사용될 수 있습니다.
```kotlin
inscpectionType.text = InspectionType.AHEAD
inscpectionType.setTextColor(Color.RED)
```
