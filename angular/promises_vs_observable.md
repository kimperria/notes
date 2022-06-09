# Promises vs Observables

This article defines and points out difference between promises and observables in JavaScript.

---

**N/B** JavaScript is a single threaded programming language, what this mean is that code written in JS is executed line by line when run. This brings about the [asynchrounous](https://www.w3schools.com/js/js_asynchronous.asp) data concept.
## Promise
A [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) is defined as placeholder for a future value.

A promise is always in one of these states:
- Pending
- Fulfilled (resolve)
- Unfulfilled (reject)

A promise is returned asynchronously inside the function that it has been declared.

## Observable
[Observable](https://rxjs.dev/guide/observable) is used to perform asynchronous operations and handle asynchronous data.

## Difference between promise and observable
| Promise | Observable |
|---------------------------------------------|------------|
| Promise in an in-built JavaScript asychronous feature defined but the Promise keyword. | Observables are imported to from the [RxJS](https://rxjs.dev/guide/overview) library. |
| They execute immediately on creation | Run after a [subscription](https://rxjs.dev/guide/subscription). They are termed lazy since they are executed only after a subcribe method has been defined. |
| Emit a single value from data fetched/consumed/requested. | Emit mulitple values over a period of time |
| Promise do not have operators | Persives data as an array. Therefore data can be manupilated using [operators](https://rxjs.dev/guide/operators) such as filter and pipe method|
| Promise cannot be canceled or stopped since it only give a response once. | Observables can be canceled using the unsubscribe feature. |
