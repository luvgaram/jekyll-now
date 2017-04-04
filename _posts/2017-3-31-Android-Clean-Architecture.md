---
layout: post
title: Mobile tech news translation
---

### Clean Architecture in Android

Droid Knights의 두 번째 세션 `Clean Architecture in Android` 영상 정리글을 작성했습니다. [Realm 공식홈페이지](https://realm.io/kr/news/clean-architecture-in-android/)에 발행됐습니다.

* 뱅크샐러드 제작사 레이니스트 CTO 황성현님 발표
* 변화에 잘 적응하려면 구조가 간결하게 분리돼야 한다가 핵심
* 어떻게 분리할 것인가? [영감 받은 블로그](https://fernandocejas.com/2014/09/03/architecting-android-the-clean-way/)
![..](https://fernandocejas.com/assets/migrated/clean_architecture1.png)

* Presentation / Data / Domain / Entity 레이어로 분리
* 상위 레이어는 하위 레이어를 알지만 반대로는 모르도록 분리할 것, 상위 레이어의 변경이 하위 레이어에 영향을 미치지 않도록!
* 자세한 코드와 각 레이어간 설계 설명은 다음주에 [Realm 공식홈페이지](https://realm.io/kr/news)에 발행 후 정리글 주소에서
