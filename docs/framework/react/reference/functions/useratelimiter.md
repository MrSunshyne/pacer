---
id: useRateLimiter
title: useRateLimiter
---

<!-- DO NOT EDIT: this page is autogenerated from the type comments -->

# Function: useRateLimiter()

```ts
function useRateLimiter<TFn>(fn, options): RateLimiter<TFn>
```

Defined in: [react-pacer/src/rate-limiter/useRateLimiter.ts:48](https://github.com/TanStack/pacer/blob/main/packages/react-pacer/src/rate-limiter/useRateLimiter.ts#L48)

A low-level React hook that creates a `RateLimiter` instance to enforce rate limits on function execution.

This hook is designed to be flexible and state-management agnostic - it simply returns a rate limiter instance that
you can integrate with any state management solution (useState, Redux, Zustand, Jotai, etc).

Rate limiting is a simple "hard limit" approach that allows executions until a maximum count is reached within
a time window, then blocks all subsequent calls until the window resets. Unlike throttling or debouncing,
it does not attempt to space out or collapse executions intelligently.

For smoother execution patterns:
- Use throttling when you want consistent spacing between executions (e.g. UI updates)
- Use debouncing when you want to collapse rapid-fire events (e.g. search input)
- Use rate limiting only when you need to enforce hard limits (e.g. API rate limits)

The hook returns an object containing:
- maybeExecute: The rate-limited function that respects the configured limits
- getExecutionCount: Returns the number of successful executions
- getRejectionCount: Returns the number of rejected executions due to rate limiting
- getRemainingInWindow: Returns how many more executions are allowed in the current window
- reset: Resets the execution counts and window timing

## Type Parameters

• **TFn** *extends* `AnyFunction`

## Parameters

### fn

`TFn`

### options

`RateLimiterOptions`\<`TFn`\>

## Returns

`RateLimiter`\<`TFn`\>

## Example

```tsx
// Basic rate limiting - max 5 calls per minute
const { maybeExecute } = useRateLimiter(apiCall, {
  limit: 5,
  window: 60000,
});

// Monitor rate limit status
const handleClick = () => {
  const remaining = getRemainingInWindow();
  if (remaining > 0) {
    maybeExecute(data);
  } else {
    showRateLimitWarning();
  }
};
```
