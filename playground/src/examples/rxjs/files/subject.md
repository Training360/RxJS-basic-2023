<!--
name:		
title:		subject
pageTitle:	subject — RxJS Observable method example + marble diagram
desc:		subject is a special type of observables
docsUrl:	https://www.learnrxjs.io/learn-rxjs/subjects/subject
-->

An RxJS Subject is a special type of Observable that allows values to be multicasted to many Observers. While plain Observables are unicast (each subscribed Observer owns an independent execution of the Observable), Subjects are multicast.

```js
const { rxObserver } = require('api/v0.3');
const { Subject } = require('rxjs');

const sub = new Subject();

sub.next(1);

sub.subscribe(rxObserver(`Subscriber A`));

sub.next(2);

sub.subscribe(rxObserver(`Subscriber B`));

sub.next(3);
```