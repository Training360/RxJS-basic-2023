<!--
name:		
title:		AsyncSubject
pageTitle:	AsyncSubject — RxJS Observable method example + marble diagram
desc:		emits its last value on completion
docsUrl:	https://rxjs.dev/guide/subject#asyncsubject
-->

The AsyncSubject is a variant where only the last value of the Observable execution is sent to its observers, and only when the execution completes.

```js
const { rxObserver } = require('api/v0.3');
const { AsyncSubject } = require('rxjs');

const subject = new AsyncSubject();

subject.subscribe(rxObserver(`observerA`));

subject.next(1);
subject.next(2);
subject.next(3);
subject.next(4);

subject.subscribe(rxObserver(`observerB`));

subject.next(5);
subject.complete();
```