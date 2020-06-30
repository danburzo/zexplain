# DOM tools

DOM helper functions to debug web pages.

## Usage

In the browser's console, import the module:

```js
// import and assign to the global `dt` variable:
import('https://danburzo.github.io/dom-tools/api.js').then(m => dt = m);

// use the API:
dt.highlight(el => el.tagName === 'LI');
```

> __Note:__ This will not work on web pages whose CSP settings disable loading external scripts. Currently looking for a workaround!

## API

* __stackingCtx__(_element_)
* __getEvents__(_element_) — (Chrome only) returns an array of events for a DOM element;
* __poking__(_element_) — returns whether the element pokes outside the bounds of the window, causing a horizontal scrollbar to appear;
* __highlight__(_predicate_, _label_) — highlight all DOM elements matching the `predicate` function;
* __all__() — returns an array of all DOM elements
## Recipes

### Get all DOM events from the page

```js
import { all, getEvents } from 'https://danburzo.github.io/dom-tools/api.js';

all().map(getEvents).flat();
```

### Highlight all stacking contexts

```js
import { highlight, stackingCtx } from 'https://danburzo.github.io/dom-tools/api.js';

highlight(stackingCtx, el => {
	let ctx = stackingCtx(el); 
	return `reason: ${ctx[0]}; z-index: ${ctx[1]}`;
});
```