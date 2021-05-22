# UTF-8

## ASCII Code 와 Unicode

우리는 어떻게 decimal number 를 binary code 로 바꾸는지 알고 있습니다. 182 -> 10110110.  
그렇다면 문자는 어떻게 binary code로 바꿀 수 있는 것일까요?   

키보드를 한번 살펴봅시다. 각각의 키는 어떤 숫자와 연결되어 있습니다. 우리가 어떤 키를 치던간에 문자는 decimal number(십진수)와 mapping됩니다.   
예로 대문자 A는 십진수로 65이고, 이를 이진수로 변환하면 1000001이 되어 컴퓨터가 인식할 수 있습니다.   
이렇게 쓰기로 약속하고 이 체계를 표로 정리한 것이 바로 ASCII Code입니다.   
ASCII Code는 7비트로 표현됩니다. 즉 127개의 서로 다른 숫자를 표현할 수 있습니다.   
이 127개의 숫자로 알파벳 대문자, 소문자 그리고 0~9까지의 숫자, 그리고 몇 가지의 symbol을 표현할 수 있습니다.  
추가적으로 몇가지 command(명령어)를 살펴보면..   
   
backspace는 0001000(8)   
escape는 0011011(27)   
Tab -> 0001001(9)   
Enter -> 001101(13)   
Delete 111111(127)   
이렇게 mapping되어 있고, Delete는 127로 ASCII Code로 표현할 수 있는 마지막 문자입니다.

(Extended ASCII - > 8 bits)

그런데 여기에는 문제점이 있습니다. 바로 ASCII 표준에 포함되지 않는 다른 문자, 예를 들어 Greek, Hebric, Arabic, Korean, Japanese, Chinese, Emoji 등을 표현할 수 없다는 것입니다.   
이 문제점을 해결하기 위해서 Unicode를 사용합니다. Unicode는 문자들이 숫자들과 연결되어있다는 점에서는 같지만, ASCII보다 더 많은 bits를 사용할 수 있다는 점에서 차이가 있습니다.   
Unicode는 더 확장되어서 8, 16, 32bits 로도 사용할 수 있는데요, 32bits를 사용할 수 있다는 것은 2,147,483,647개의 문자를 나타낼 수 있다는 것을 의미합니다.   
확실히 127개까지 표현할 수 있는 ASCII에 비해 어마어마한 양이죠?

<br>

## Encoding

유니코드에서는 일단 첫 번째 단계로, 모든 문자들을 integers와 매핑합니다.   
아직 이 정수를 어떻게 매모리에 할당 할지, 이 정수를 표현하기 위해서 몇 bytes를 사용해야할 지는 정해지지 않았습니다.   
예로 A는 정수 65와 매핑된다고 합시다. 이때 65는 code point라고 부릅니다.   
65는 decimal code point, 100001 binary code point라고 합니다. 이것은 아직 메모리에 어떻게 표현될지 정해지지 않은 상태입니다.   
이것을 어떻게 표현할지 정하면, 정한 것에 따라 인코딩 방식도 달라집니다.   

3가지의 대표적인 encoding 방식이 바로 Utf-32, Utf-16, Utf-8 입니다.   
이 방식들이 가장 널리 사용되는 인코딩 시스탬이고, 사람들은 이것을 쓰자고 약속한 것입니다. 특히 Utf-8은 웹 어플리케이션 세계에서 대표적으로 쓰이고 있습니다.   

<br>

### Utf-8 encoding

Utf-16와 마찬가지로 Utf 8의 8은 고정된 값이 아닙니다.  Utf-8은 multi byte character set입니다.
8비트(1byte), 16비트(2byte), 24비트(3byte), 32비트(4byte)를 표현할 수 있습니다.

그렇다면 utf-8체계에서 디코딩을 할 때, 이것이 어떤 바이트로 encoding이 되었는지 알아야합니다.
이를 위해 몇 까지 marker가 존재하는데요, 만약 첫 번째 bit가 0이라면 이것은 1byte로 인코딩되었다고 짐작할 수 있습니다.
이러한 경우는 아스키 코드가 0 ~ 127까지 표현 가능하기 때문에 Backward compatibile with ascii 라고 볼 수 있습니다.   

<br>

Code point가 127보다 크면 multi-byte sequence를 사용해야할 것입니다.   
만약 인코딩 된 바이트가 110으로 시작하면,(110xxxxx) 이것은 문자가 2bytes로 인코딩 되었다는 것을 의미합니다. 
110XXXXX | 10XXXXXX
Leading byte -> 어떤 바이트로 인코딩 되었는지 알려줌
continuation byte -> 맨 앞에 10으로 표기됨

만약 3바이트로 인코딩 되었다면? 
Leading byte는 1110으로 시작 뒤에 2개의 continuous byte가 있습니다.
예: 1110XXXX 10XXXXXX 10XXXXXX

만약에 4bytes가 인코딩될 때 사용되었다면?
Leading byte는 11110으로 시작 뒤에 3개의 continuous byte가 있습니다.
예: 11110XXX 10XXXXXX 10XXXXXX 10XXXXXX
