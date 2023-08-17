<!--
name:		
title:		fromEvent
pageTitle:	fromEvent — RxJS function example + marble diagram
desc:		Learn how to turn an Event into an Observable using "fromEvent"
docsUrl:	https://rxjs.dev/api/index/function/from
-->

Turn event into an observable sequence. These events can be window, element, or custom events.

```js
const { rxObserver } = require('api/v0.3');
const { fromEvent } = require('rxjs');
const { map } = require('rxjs/operators');

// create a new button element
const button = document.createElement('button');

//create observable that emits click events
const source = fromEvent(button, 'click');

//map to string with given event timestamp
const example = source.pipe(
    map(event => Math.floor(event.timeStamp / 1000))
);

const subscribe = example.subscribe(rxObserver());

setTimeout( () => {
    button.dispatchEvent( new Event('click') );
}, 500);

```
