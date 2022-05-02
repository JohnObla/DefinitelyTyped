All the Ramda types have been replaced with the "AnyFn"
```
  export type AnyFn = (...args: any[]) => any;
```
This stops typescript from clashing with Ramda completely.