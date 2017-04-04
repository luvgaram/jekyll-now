---
layout: post
title: Realm JavaScript, RMP Node.js Server
---

### RMP Node.js Server

```javascript

let QuestionSchema = {
  name: 'Question',
  primaryKey: 'id',
  properties: {
    id: 'int',
    status: {type: 'bool', default: true},
    timestamp: 'date',
    question: 'string',
    author: {type: 'User'},
    vote: {type: 'list', objectType: 'User'},
    isAnswered: {type: 'bool', default: false},
  }
}

```

Realm QnA 서버에서 사용하는 Schema 변경, User 추가
User가 있으면 사용하고 아니면 만들기 위해 predicate를 만들다가 삽질을 했습니다. 결론은 따옴표가 필요하다!
필터링을 위한 predicate 예제

```javascript

   var pred = 'id = "' + sess.author + '"' 
   let newAuthor =  syncRealm.objects('User').filtered(pred)
   
```

이제 RMP를 위한 Node.js 서버에서 Create와 Read는 대충 다 된것 같고 Update와 Delete를 만들면 끝인데 프론트를 예쁘게 만들려면 또 고민입니다.
