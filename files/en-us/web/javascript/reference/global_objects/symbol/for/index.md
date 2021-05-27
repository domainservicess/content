---
title: Symbol.for()
slug: Web/JavaScript/Reference/Global_Objects/Symbol/for
tags:
- ECMAScript 2015
- JavaScript
- Method
- Symbol
browser-compat: javascript.builtins.Symbol.for
---
{{JSRef}}

The **`Symbol.for(key)`** method searches for existing symbols in a runtime-wide
symbol registry with the given key and returns it if found. Otherwise a new
symbol gets created in the global symbol registry with this key.

{{EmbedInteractiveExample("pages/js/symbol-for.html")}}

## Syntax

<pre class="brush: js">Symbol.for(<var>key</var>);</pre>

### Parameters

- `key`
  - : String, required. The key for the symbol (and also used for the
    description of the symbol).

### Return value

An existing symbol with the given key if found; otherwise, a new symbol is
created and returned.

## Description

In contrast to `Symbol()`, the `Symbol.for()` function creates a symbol
available in a global symbol registry list. `Symbol.for()` does also not
necessarily create a new symbol on every call, but checks first if a symbol with
the given `key` is already present in the registry. In that case, that symbol is
returned. If no symbol with the given key is found, `Symbol.for()` will create a
new global symbol.

### Global symbol registry

The global symbol registry is a list with the following record structure and it
is initialized empty:

<table class="standard-table"><caption>A record in the global symbol registry</caption><tbody><tr><th>Field name</th><th>Value</th></tr><tr><td>[[key]]</td><td>A string key used to identify a symbol.</td></tr><tr><td>[[symbol]]</td><td>A symbol that is stored globally.</td></tr></tbody></table>

## Examples

### Using Symbol.for()

```js
Symbol.for('foo'); // create a new global symbol
Symbol.for('foo'); // retrieve the already created symbol

// Same global symbol, but not locally
Symbol.for('bar') === Symbol.for('bar'); // true
Symbol('bar') === Symbol('bar'); // false

// The key is also used as the description
var sym = Symbol.for('mario');
sym.toString(); // "Symbol(mario)"
```

To avoid name clashes with your global symbol keys and other (library code)
global symbols, it might be a good idea to prefix your symbols:

```js
Symbol.for('mdn.foo');
Symbol.for('mdn.bar');
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Symbol.keyFor()")}}
