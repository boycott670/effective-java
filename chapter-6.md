# Chapter 6: Enums and Annotations

## Item 30: Use enums instead of int constants

The advantages of enum types over int constants are compelling. Enums are far more readable, safer, and more powerful. Many enums require no explicit constructors or members, but many others benefit from associating data with each constant and providing methods whose behavior is affected by this data. Far fewer enums benefit from associating multiple behaviors with a single method. In this relatively rare case, prefer constant-specific methods to enums that switch on their own values. Consider the strategy enum pattern if multiple enum constants share common behaviors.

## Item 31: Use instance fields instead of ordinals

Most programmers will have no use for this method. It is designed for use by general-purpose enum-based data structures such as EnumSet and EnumMap. Unless you are writing such a data structure, you are best off avoiding the ordinal method entirely.

## Item 32: Use EnumSet instead of bit fields

Just because an enumerated type will be used in sets, there is no reason to represent it with bit fields. The `EnumSet` class combines the conciseness and performance of bit fields with all the many advantages of enum types described in [Item 30](chapter-6.md#item-30-use-enums-instead-of-int-constants). The one real disadvantage of `EnumSet` is that it is not, as of release 1.6, possible to create an immutable `EnumSet`, but this will likely be remedied in an upcoming release. In the meantime, you can wrap an `EnumSet` with `Collections.unmodifiableSet`, but conciseness and performance will suffer.

## Item 33: Use EnumMap instead of ordinal indexing

It is rarely appropriate to use ordinals to index arrays: use `EnumMap` instead.

## Item 34: Emulate extensible enums with interfaces

While you cannot write an extensible enum type, you can emulate it by writing an interface to go with a basic enum type that implements the interface. This allows clients to write their own enums that implement the interface. These enums can then be used wherever the basic enum type can be used, assuming APIs are written in terms of the interface.