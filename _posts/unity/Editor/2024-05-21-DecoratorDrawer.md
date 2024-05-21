---
layout: single
title:  "유니티 DecoratorDrawer"
categories: 
    - Unity
tag: [Unity, Editor]
published: true

author_profile: true # 옆에뜨는 프로파일

search: true #검색해도 안뜨게함

date: 2024-05-21
last_modified_at: 2024-05-21

---

## DecoratorDrawer 란
유니티에서는 Editor에서 보여지는 여러 요소들을 `커스터마이징` 할 수 있도록 도와준다. 

여기서 볼 DecoratorDrawer는 그 중 한가지로, property를  데이터를 기반으로 `장식적인 요소`를 그리는 것이다. `(property 자체를 그리는 것이 아님)`

즉, 속성 주변을 꾸며주는 기능이라고 보면 된다.

## 사용 상황
일반적으로 인스펙터 창에서 보여지는 변수들은 다음과 같이 밋밋하다.

![image](https://github.com/novicehog/comments/assets/131991619/9c569660-5b09-4630-a384-f7d099e8351d)
<br>

이 때 DecoratorDrawer를 통해 제목과 밑줄을 그어주는 기능을 커스터마이징하여 적용하면 다음과 같이 변수들이 보기좋게 된다.

![image](https://github.com/novicehog/comments/assets/131991619/9e667a10-d201-415f-a6bd-72b3d68bc6c4)
<br>

여기서 DecoratorDrawer를 통해 만들어진 부분은 다음과 같이 변수 자체가 아니라 변수 장식인 제목과 밑줄이다.

<img width="159" alt="image" src="https://github.com/novicehog/comments/assets/131991619/e941f1de-8336-4d3f-99e0-9b31d14b2987">