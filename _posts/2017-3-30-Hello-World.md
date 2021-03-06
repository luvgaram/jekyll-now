---
layout: post
title: GitHub Blog Setting
---

### 블로그

[참고 사이트](http://thdev.net/653)를 보고 GitHub 블로그를 설정했습니다.

* barryclark/jekyll-now 포크해서 간단하게 구성

### RealmQnA 토이 프로젝트

Realm 모바일 플랫폼 + Node.js로 간단한 읽기와 세션 기반 사용자 식별이 되는 웹서버를 구축했습니다.

* realm: 모바일 데이터베이스 + 오브젝트 서버 = 실시간 동기화
* express
* body-parser
* express-session: 세션
* express-handlebars: 시맨틱 탬플릿
* nodemon: 자동 서버 재시작
    
express-handlebars에 동등 비교 로직은 [StackOverflow #1](http://stackoverflow.com/questions/8853396/logical-operator-in-a-handlebars-js-if-conditional),  helper 넣기는 [StackOverflow #2](http://stackoverflow.com/a/39297850) 참고.
```javascript

var handlebars = require('express-handlebars').create({
  helpers: {
    ifCond: function(v1, v2, options) {
      if(v1 === v2) {
        return options.fn(this);
      }
      return options.inverse(this);
    }
  }
});

```

Realm에서 sync user 로그인하고 오브젝트 서버의 Realm을 사용하는 코드

```javascript

Realm.Sync.User.login(SERVER_URL, user, password, (error, user) => {
    var syncRealm;

    if (!error) {
      var syncRealm = new Realm({
        sync: {
          user: user,
          url: REALM_URL,
        },
        schema: [QuestionSchema]
      });

      let questions = syncRealm.objects('Question').sorted('id', true);
      res.render(///);
    }
  });
});

```

## 회고

오랜만에 노드를 보니 하나도 모르겠고 재밌습니다. github edit 기능은 한글을 전혀 배려 안하는군요. 에디터야, 괴롭혀서 미안 :(

## TO-DO

* [편리한 깃헙페이지 블로깅을 위한 이미지서버, 구글드라이브: 업로드 ShellScript편](https://beomi.github.io/2017/03/27/Use-GoogleDrive-as-Image-Server/) 따라해볼 예정!
* vote 기능을 넣으려면 RealmQnA 스키마를 고쳐야할듯
* 세션으로 사용자를 판가름해서 vote와 edit 기능 추가. 그런데 handlebars가 이런 로직에 적합한지 고민이 됩니다. if문도 없어서 당황... 다른 템플릿을 찾아 봐야?
