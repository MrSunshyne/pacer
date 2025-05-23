---
id: SolidDebouncer
title: SolidDebouncer
---

<!-- DO NOT EDIT: this page is autogenerated from the type comments -->

# Interface: SolidDebouncer\<TFn\>

Defined in: [debouncer/createDebouncer.ts:11](https://github.com/TanStack/pacer/blob/main/packages/solid-pacer/src/debouncer/createDebouncer.ts#L11)

An extension of the Debouncer class that adds Solid signals to access the internal state of the debouncer

## Extends

- `Omit`\<`Debouncer`\<`TFn`\>, `"getExecutionCount"` \| `"getIsPending"`\>

## Type Parameters

• **TFn** *extends* `AnyFunction`

## Properties

### executionCount

```ts
executionCount: Accessor<number>;
```

Defined in: [debouncer/createDebouncer.ts:13](https://github.com/TanStack/pacer/blob/main/packages/solid-pacer/src/debouncer/createDebouncer.ts#L13)

***

### isPending

```ts
isPending: Accessor<boolean>;
```

Defined in: [debouncer/createDebouncer.ts:14](https://github.com/TanStack/pacer/blob/main/packages/solid-pacer/src/debouncer/createDebouncer.ts#L14)
