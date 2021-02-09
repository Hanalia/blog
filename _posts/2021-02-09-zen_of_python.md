---
typora-root-url: https://Hanalia.github.io/blog/_posts
title:  "파이썬의 기본 이념 : The Zen of Python"
date:   2021-02-09
excerpt: 파이썬의 숨겨진 이스터에그(Easter Egg) 해석
categories: Python
tags: [Python,IT]


---



## 파이썬의 이스터에그(Easter Egg)?

혹시 파이썬이 컴퓨터에 설치되어 있으면 터미널에 아래와 같이 입력해 본다.



```bash
python -m this.py
```



파이썬이 켜져있으면 아래와 같이 입력해도 된다

````python
import this
````



그려면 아래와 같이 나온다.

![Screen Shot 2021-02-09 at 8.16.44 PM](https://i.loli.net/2021/02/09/NkgJvpuSXDYydG8.png)

파이썬의 철학이라고 하는 The Zen of Python.

모든 파이썬에 기본으로 장착되어 있는 이 문구는 도대체 어떤 의미를 지니는 것일까?

간단하게 해석해 본다.



> **Beautiful is better than ugly.**

코드도 다른 글쓰기와 마찬가지로 코드를 작성하는 사람이 있는 반면, 그 코드를 읽고 이해하는 사람도 
반드시 있다. 여기서 Beautiful라는 의미는 남들이 보기 편하다, 즉 **'가독성이 좋다'**로 이해할 수 있다.



> **Explicit is better than implicit.**

아무런 배경지식이 없는 사람도 잘 이해할 수 있을 만큼 내용이 분명하게 드러나는 글이 좋은 글이다.

코드도 마찬가지다. 내포된 의미가 많을 수록 이해하기 어려워진다. 모든 것을 겉으로 드러내자.



> **Simple is better than complex.**
>
> **Complex is better than complicated.**

항상 심플함, 단순함을 추구하되, 심플함의 한계는 인정하자.

대신 이해하기 어렵고 '복잡한' 수준이 되지는 않도록 주의를 하자.



> **Flat is better than nested.**

체계를 갖추기 위해서 카테고리별로 폴더를 만들고 그 안에 폴더를 만들어본 경험은 모두들 있을 것이다.

하지만 이런 체계를 갖추는 것보다 체계가 없는 플랫(Flat)한 상태로 내버려 두는 것이 좋을 때가 있다.

과도한 디렉토리 생성은 오히려 복잡함만 야기할 수 있다.



> **Sparse is better than dense.**

위의 'simple is better than complex'와 유사하다.

어떤 프로그래머는 효율을 강조하기 위해서 최대한 다양한 기능들을 한 문장, 또는 하나의 함수(Function)에 구겨넣는 경우가 있다.

이런 경우보다 여러 줄에 걸쳐서 코드를 작성하는 것이 코드를 읽는 사람 입장에서 좋을 수 있다.





> **Readability counts.**

특히 변수나 함수의 이름을 설정할 때 중요한 말이다. 다른 사람이 strcmp()라는 함수를 보았을 때
"String Compare"(문자열 비교)라는 내용을 떠올릴 수 있을지 의문이다. 차라리 compareString()으로
함수 명을 설정하는 것이 나을 수 있다.



> **Special cases aren't special enough to break the rules.**
>
> **Although practicality beats purity.**

사실 이 두가지는 상충되는 의미를 가지고 있다. 프로그래밍 언어에서 기본적으로 추구하는 원칙을 고수하는 것이 중요하지만 (첫번째 문장), 때로는 그 순수한 원칙을 어기는 것이 중요할 수 있다. (두번째 문장)
예를 들어 자바(Java) 의 경우 모든 요소를 객체 지향 패러다임(Object-Oriented-Paradigm) 으로 처리하려고 
하는 습성때문에 아주 간단한 기능을 수행하는 코드도 복잡해진다.
파이썬은 이처럼 지나친 원칙이나 이념의 고수는 지양한다.



> **Errors should never pass silently.** 
>
> **Unless explicitly silenced.**

에러 처리 (Error Handling)는 코딩하면서 가장 답답하고 힘이 드는 부분이다. 
하지만 에러가 바로바로 등장해서 코드가 작동이 되지 않는 경우가 에러를 무시하고 앞으로 나아가는 경우보다 낫다. 초반에 무시된 에러는 결국 어떻게든 발견되고 말썽을 일으킬 것이기 때문이다. 



> **In the face of ambiguity, refuse the temptation to guess.**

문제 해결을 위해서 이것저것 아무 방법을 시도하다가 우연히 문제가 해결되는 경우가 있다.
이런 식의 문제해결법에는 한계가 있다.
코드가 작동하지 않는다면, 신중하게 문제의 원인이 무엇인지 명확히 분석하고 그 원인을 찾아야 한다.



> **There should be one-- and preferably only one --obvious way to do it.**

파이썬이 간결하고 배우기 쉬운 언어라고 하는 이유가 여기에도 있는 것 같다.
파이썬에서는 특정한 기능을 수행하기 위해서 가장 효율적인 '한 가지'방식을 지향한다.
반대로 펄(Perl) 언어의 모토는 'There's more than one way to do it!'이다.
언어의 유연성을 생각하면 한가지 기능을 수행하는 데 다양한 방식이 있으면 좋을 것 같지만,
이 경우 다른 사람들의 코드를 읽고 이해하기 위해서 그 모든 방식을 다 알고 있어야 하는 치명적인 단점이 있다.



> **Although that way may not be obvious at first unless you're Dutch.**

그냥 가벼운 농담이라고 한다.... 참고로 파이썬의 창시자 Guido van Rossum은 네덜란드인(Dutch)이다.



> **Now is better than never. Although never is often better than *right* now.**

정확성과 신속성, 이 두가지는 항상 상충관계에 있다.

너무 정확성을 추구하느라 코드가 계속 지연되는 것 보다는 일단 지금 실행할 수 있는 코드를 작성하는 것 같다.

하지만 아무리 신속함이 중요하더라도 그 코드가 너무 엉망투성이면 차라리 코드가 충분히 완성될 때 까지 기다리는 편이 나을 수 있다.



> **If the implementation is hard to explain, it's a bad idea.**
>
> **If the implementation is easy to explain, it may be a good idea.**

누군가에게 내용을 설명하기가 복잡하고 어려운 코드는 나쁜 코드다.
누군가에게 내용을 설명하기가 쉬운 코드는 좋은 코드다.
그런데 이렇게 코드를 설명하기 쉽게 짜는 것도 능력이다...



> **Namespaces are one honking great idea -- let's do more of those!"**

네임스페이스(Namespace)는 이름들이 서로 상충되지 않도록 이름을 서로 분리해서 담은 공간이다.
예를 들어 open()과 webbrowser.open()의 open은 서로 같은 'open'이지만 네임스페이스가 달라서
(전자는 전체에 내장된 built-in namespace,  후자는webbrowser라는 모듈의 namespace) 서로 상충되지
않는다. 이렇게 네임스페이스를 활용해서 각 변수, 함수들의 명칭이 서로 상충되지 않도록 하자.





 파이썬에 막 입문한 사람이든, 파이썬을 익숙하게 다루는 사람이든, 아니면 프로그래밍 언어에 능숙한 개발자든
이 Zen of Python에서 얻는 바가 조금씩 다를 것이다.

파이썬을 배우는 각 단계에 따라서 문장 하나 하나가 다르게 와닿을 수도 있을 것 같다.

짧지만 핵심을 찌르는 통찰력 있는 문구다.











