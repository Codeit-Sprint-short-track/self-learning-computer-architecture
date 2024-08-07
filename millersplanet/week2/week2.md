# Chapter 02 데이터

### 02-1 0과 1로 숫자를 표현하는 방법
- **비트**는 0과 1로 표현할 수 있는 가장 작은 정보 단위
- **이진법**은 0과 1만으로 수를 표현하는 방법
- 이진법에서 음수는 2의 보수로 표현할 수 있으며, 컴퓨터 내부에서는 수가 양수인지 음수인지 구분하기 위해 **플래그** 사용
- 이진법을 사용하면 숫자가 너무 길어진다는 단점을 해결하기 위해 **십육진법** 사용
- 십육진수 한 글자를 4비트의 이진수로 간주하여 변환
- 프로그래밍할 때 십육진수를 직접 써넣는 경우도 많음

### 02-2 0과 1로 문자를 표현하는 방법
#### 용어
- 문자 집합: 컴퓨터가 인식하고 표현할 수 있는 문자의 모음
- 문자 인코딩: 문자를 0과 1로 변환하는 과정. 같은 문자 집합에 대해서도 다양한 인코딩 방법이 있을 수 있음
- 문자 디코딩: 0과 1로 이루어진 문자 코드를 사람이 이해할 수 있는 문자로 변환하는 과정

#### 아스키 코드 (ASCII)
- 초창기 문자 집합 중 하나로, 아스키 문자는 각각 7비트로 표현된다.
- 알파벳, 아라비아 숫자, 일부 특수 문자를 포함하여 128개 문자 표현 가능

#### EUC-KR
- 한글의 특수성으로 인해 한글 인코딩에는 완성형과 조합형의 두 가지 방식이 존재한다.
- EUC-KR은 대표적인 완성형 인코딩 방식으로, 초성, 중성, 종성이 결합된 한 글자에 2바이트 크기의 코드를 부여한다.
- 모든 한글 조합을 표현할 수 없어 CP949가 등장했으나 여전히 한글 전체를 표현할 수 없었다.

#### 유니코드와 UTF-8
- 유니코드는 여러 나라의 문자들을 광범위하게 표현할 수 있는 _통일된_ 문자 집합
- 유니코드는 글자에 부여된 값 자체를 인코딩된 값으로 삼지 않고 이 값을 다양한 방법으로 인코딩한다.
- 인코딩 방법으로 UTF-8, UTF-16, UTF-32 등이 있고 **UTF-8**이 가장 대중적이다.