<!--
name:		
title:		mergeMap (aka flatMap)
pageTitle:	mergeMap — RxJS (flatMap) operator example + marble diagram
desc:		mergeMap will substitute value on the source Observable with an Observable, returned by inner function. See this example of RxJS mergeMap with a timer
docsUrl:	https://rxjs.dev/api/operators/mergeMap
-->

`mergeMap`, as well as other `**Map` operators, will substitute value on the source stream with a stream of values, returned by inner function. When source stream emits, `mergeMap` will call inner function to merge yet another inner stream to the resulting stream.  

> Also try this [mergeMap vs exhaustMap vs switchMap vs concatMap](/rxjs/mergeMap-vs-exhaustMap-vs-switchMap-vs-concatMap/) head-to-head comparison

```js
const { rxObserver, palette } = require('api/v0.3');
const { from, of } = require('rxjs');
const { mergeMap } = require('rxjs/operators');

// helper to create promise
const myPromise = val =>
  new Promise(resolve => resolve(val));

// emit 'Hello'
const source$ = of( 
    Math.floor(Math.random() * 10) 
);

// map to promise and emit result
source$.pipe(
    mergeMap(val => myPromise(val))
).subscribe(rxObserver());

```

**NOTE:** `mergeMap` is also available via `flatMap` alias