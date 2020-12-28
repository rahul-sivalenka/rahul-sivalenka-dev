---
title: TypeScript Deep Partial
date: "2020-12-21T10:00:00.000Z"
description: "Generic type to allow nested partial objects."
tags: ["Today I Learned", "TypeScript"]
---

## Problem

In TypeScript (TS), [`Partial<T>`](https://www.typescriptlang.org/docs/handbook/utility-types.html#partialtype) utility type can be used to make all the properties of a `T` as optional. However, the problem here is it only makes the first level properties of the type `T` as optional.

For example, let's say we have a `Theme` type as follows:

```typescript
interface Theme {
  direction: 'ltr' | 'rtl';
  color: {
    primary: string;
    secondary: string;
    text: string;
  }
}
```

Applying `Partial` to this makes `direction` and `color` properties as optional. However, when we want to set only `primary` property of the nested object `color`, TS will throw an error saying `Type '{ primary: string; }' is missing the following properties from type '{ primary: string; secondary: string; text: string; }': secondary, text`.

```typescript
const partialTheme: Partial<Theme> = {
  direction: 'rtl',
  color: {
    // TS error: Type '{ primary: string; }' 
    // is missing the following properties from type 
    // '{ primary: string; secondary: string; text: string; }': 
    // secondary, text(2739)
    primary: '#cc7351'
  }
}
```

See Errors section in playground [here](https://www.typescriptlang.org/play?#code/JYOwLgpgTgZghgYwgAgCoAsIFsUG8BQyyAJsFBAmMAPYgBcyA5ADZhSPIA+TUYzjAbkLIE1ZtSgMCRIgAcowLHCgBPBgGc2oAOZCZydRVrFlag1pC7hRSAA8wGi1aIBffG-yiQm5LOVU4ZgxsCAYABX9gQIAeYJwAPmQAXmRpEjIKKloGFjZGABphUXFJVOtfBSVVHIBiBAQAdgBmAFYARkZhNxcgA).


## Solution

The following is a generic type which can be used to make any nested object type as partial.

```typescript
type DeepPartial<T> = {
  [P in keyof T]?: DeepPartial<T[P]>;
};

const deepPartialTheme: DeepPartial<Theme> = {
  direction: 'rtl',
  color: {
    // No TS error here
    primary: '#cc7351'
  }
}
```

See playground [here](https://www.typescriptlang.org/play?#code/JYOwLgpgTgZghgYwgAgCoAsIFsUG8BQyyAJsFBAmMAPYgBcyA5ADZhSPIA+TUYzjAbkLIE1ZtSgMCRIgAcowLHCgBPBgGc2oAOZCZydRVrFlag1pC7hRSAA8wGi1aIBffG-xgVslABEIELIACspUcMwAPKgAf
MgAvMjSyADaQcigyADWECrUMGgAugD8DP6BIbzA4VGpBdFCLkL4oiCaJAHBoVXMGNgQpR0VYZG9OLEJSaTklDT0PHyMADTCouKSidbI8oqmDIwAxAgIAOwAzACsAIyMwm4uQA).

## References

* [SO Answer: TypeScript: deep partial?](https://stackoverflow.com/a/61132308/5887448)