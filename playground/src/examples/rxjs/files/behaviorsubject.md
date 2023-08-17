<!--
name:		
title:		BehaviorSubject
pageTitle:	behaviorsubject — RxJS Observable method example + marble diagram
desc:		behaviorsubject requires an initial value and emits the current value to new subscribers
docsUrl:	https://rxjs.dev/guide/subject#behaviorsubject
-->

One of the variants of Subjects is the BehaviorSubject, which has a notion of "the current value". It stores the latest value emitted to its consumers, and whenever a new Observer subscribes, it will immediately receive the "current value" from the BehaviorSubject.

```js
const { rxObserver } = require('api/v0.3');
const { BehaviorSubject, Subject } = require('rxjs');

const subject = new BehaviorSubject(123);

// two new subscribers will get initial value => output: 123, 123
subject.subscribe(rxObserver('subscriberA'));
subject.subscribe(rxObserver('subscriberB'));

subject.next(456);

subject.subscribe(rxObserver('subscriberC'));

subject.next(789);

subject.subscribe(rxObserver('subscriberD'));
```