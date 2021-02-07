---
typora-root-url: https://Hanalia.github.io/blog/_posts
title:  "[M1] Hammerspoon에서 한영키를 키보드별로 설정하기"
date:   2021-02-07
excerpt: 간단한 스크립트를 통해서 USB에 반응하는 키전환 설정하기
categories: IT
tags: [M1,IT,Mac Os]

---





# 애증의 M1 



첫번째 애플 노트북으로 M1 맥북 에어를 선택했다.



정말 빠르고, 소음도 없고, 부족함이 하나도 없을 줄 알았던 녀석이다.



하지만 역시 M1 칩셋이 아직 안정화가 되지 않아서 문제점들이 조금씩 드러나고 있다...



### 문제점 : 한영키를 우측 커멘드로 설정하고 싶은데, 

### Karbiner-Elements이 아직 M1에서 제대로 작동을 안한다



수십년 넘게 윈도우만 사용하다가 맥북으로 넘어오니까 제일 불편한점이 한영 전환이다.

맥북에서는 한영 전환을 위해서 Caplocks를 누르거나,  좌측 커멘드+space를 눌러야 한다.

윈도우에서 사용하던 것과 가장 유사한 느낌을 가져가려면 한영 전환을 우측 커멘드로 바꿔줘야 하는데,

이 때문에 많은 맥북 유저들은 자신이 원하는 대로 키 설정을 바꿀 수 있는 Karbiner-Elements라는 앱을 많이 사용해왔다.

(https://ssossoblog.tistory.com/54)

나도 똑같이 사용해보면서 문제 없이 잘 사용한다고 생각했는데,



가만히 보니 컴퓨터를 종류해도 계속 에러 메시지가 나오고 재부팅이 된다.



![img](https://149493502.v2.pressablecdn.com/wp-content/uploads/2020/12/your-computer-was-restarted-because-of-a-problem-big-sur.jpg)



새로 산 M1 자체의 결함인 줄 알았고,

식겁했다.



다행이도 구글링을 해보니 Karbiner-Elements라는 앱과 M1칩셋 간에 충돌 현상으로 인해서 이런 오류가 발생했던 것이다.

문제를 해결하기 위해서는 이 앱을 지우는 것 밖에 없었다...



그래서 다른 대안을 찾아보았다.





### 어설픈 대안이었던 Hammerspoon



역시 이 문제를 나만 겪은 것이 아니었다.



많은 M1 유저들이 동일한 현상을 겪었고,

누구는 이에 대한 대안으로 Hammerspoon을 추천했다. [링크](https://deftkang.tistory.com/192)



사실 맥북만 있는 사람은 위 링크 내용을 따라하기만 해도 큰 문제가 없다.



하지만 집에서는 외장 키보드, 밖에서는 맥북 키보드를 사용하는 입장에서 위 링크만으로 문제가 해결되지 않았다.



외장 윈도우 키보드의 우측 alt키와 맥북의 우측 커멘드 키의 input 자체가 달라서, 매번 설정을 달리 해줘야 하는 문제가 있었다....



그래도 찾아보니 나름의 해결법이 있어서 공유한다.



### USB Event에 반응하는 함수 설정하기



그렇다... 특정 USB가 연결이 되면 반응해서 특정한 config 코드만 발동될 수 있도록 설정하는 부분이 있었다.

먼저 우측 상단의 Hammerspoon 아이콘을 클릭하고, config.lua에서 어래와 같이 입력한다.



* 참고로 본인의 디바이스 명을 확인하고 싶으면 좌측 애플 아이콘 → 이 Mac에 관하여 → 시스템 리포트 → 하드웨어의 USB 부분을 확인한다. 



````lua
-- 아무런 디바이스가 없을 때의 디폴트 키전환 값
local FRemap = require('foundation_remapping') local remapper = FRemap.new() remapper:remap('rcmd', 'f18') remapper:register()

usbWatcher = nil
-- HID Keyboard 있는 위치에 본인의 디바이스 명을 기입
function usbDeviceCallback(data)
    if (data["productName"] == "HID Keyboard") then
        if (data["eventType"] == "added") then --디바이스를 연결했을 때의 키전환 (lcmd -> f18)
            local FRemap = require('foundation_remapping') local remapper = FRemap.new() remapper:remap('lcmd', 'f18') remapper:register()
        elseif (data["eventType"] == "removed") then --다비아스를 제거했을 때의 키전환 (rcmd -> f18)
            local FRemap = require('foundation_remapping') local remapper = FRemap.new() remapper:remap('rcmd', 'f18') remapper:register()
        end
    end
end

usbWatcher = hs.usb.watcher.new(usbDeviceCallback)
usbWatcher:start()
````



이렇게 설정해주면 외장 키보드와 내장 키보드 모두 내가 원하는 키로 한영전환을 할 수 있다!



Karbiner Elements보다는 조금 복잡해 보이는 도구이지만, 파면 팔수록 유저 입장에서 커스마이징할 수 있는 기능이 많아 보인다.



