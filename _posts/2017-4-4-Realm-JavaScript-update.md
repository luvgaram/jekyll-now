---
layout: post
title: Realm JavaScript, RMP Node.js Server - delete
---

### RMP Node.js Server - update & delete

* question 데이터의 update와 delete를 구현했습니다.
* delete는 실제 데이터를 직접 지우지 않고 status를 false로 업데이트했습니다.
* form 몇년만인가!
* req body에 question이 있으면 update, 없으면 delete (실제로는 status=false)

```javascript
if (question) {
  syncRealm.write(() => {
    syncRealm.create('Question', {id: id, question: question, timestamp: timestamp}, true)
  });
} else {
  syncRealm.write(() => {
    syncRealm.create('Question', {id: id, status: false, timestamp: timestamp}, true)
  });
}
```
