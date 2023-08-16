<!--
name:		
title:		ReplaySubject
pageTitle:	ReplaySubject — RxJS Observable method example + marble diagram
desc:		ReplaySubject reaplays or emits old values to new subscribers
docsUrl:	https://rxjs.dev/guide/subject#replaysubject
-->

A ReplaySubject is similar to a BehaviorSubject in that it can send old values to new subscribers, but it can also record a part of the Observable execution.

```js
const { rxObserver } = require('api/v0.3');
const { ReplaySubject, Subject } = require('rxjs');

// buffer 3 values for new subscribers
const subject = new ReplaySubject(3); 

subject.subscribe(rxObserver(`observerA`));

subject.next(1);
subject.next(2);
subject.next(3);
subject.next(4);

subject.subscribe(rxObserver(`observerB`));

subject.next(5);
```