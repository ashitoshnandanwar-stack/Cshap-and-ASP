# C# Quick Notes (Condensed)

## Memory & .NET Basics

-   **Value Types** (int, float, struct, enum): store data directly,
    usually stack, copied by value.
-   **Reference Types** (class, array, string): store reference, heap,
    copied by reference.
-   **CTS**: how .NET defines and manages types.
-   **CLS**: rules for language interoperability.
-   **ILDASM**: view IL, metadata, manifest of assemblies.

  Stack                Heap
  -------------------- ------------
  Fast, auto-managed   GC managed
  Local values         Objects
  Fixed size           Dynamic

------------------------------------------------------------------------

## Methods

-   **Overloading**: same name, different parameters (return type alone
    not allowed).
-   **Optional Params**: default values, must be last.
-   **Named Params**: order independent.
-   **params**: variable arguments, last parameter, array.
-   **Local Functions**: methods inside methods (helper logic).

------------------------------------------------------------------------

## Properties & Encapsulation

-   Properties = safe access to fields using `get` / `set`.
-   Readonly: only `get`, assign via constructor or computed.
-   Encapsulation = hide data + controlled access.

------------------------------------------------------------------------

## Constructors & Object Lifecycle

-   Constructor: same name as class, no return, auto-called.
-   Types: Default, Parameterized, Static (runs once).
-   Object Initializer: set properties at creation.
-   Destructor (`~Class`): non-deterministic cleanup.
-   **IDisposable**: deterministic resource release (`Dispose`,
    `using`).

------------------------------------------------------------------------

## Static Members

-   Belong to class, one copy, accessed via class name.
-   Static fields, methods, properties, constructors.
-   Static class: only static members, cannot instantiate.

------------------------------------------------------------------------

## Inheritance & Polymorphism

-   `class D : B`
-   Base constructor runs first.
-   **Overloading**: different signature.
-   **Hiding**: `new` keyword (compile-time).
-   **Overriding**: `virtual` + `override` (runtime).
-   `sealed` method: cannot be overridden further.
-   **Abstract class**: cannot instantiate; may contain abstract
    methods.
-   **Interface**: contract, multiple inheritance, all public.

  Feature   Overload   Override           Hide
  --------- ---------- ------------------ ---------
  Binding   Compile    Runtime            Compile
  Keyword   --         virtual/override   new

------------------------------------------------------------------------

## Interfaces

-   Implement all members, methods must be public.
-   Explicit implementation resolves name conflicts.
-   Default interface methods (C# 8+): backward compatibility.

------------------------------------------------------------------------

## Operators, Types

-   Operator overloading: static, at least one user type.
-   `struct`: value type, no inheritance from classes.
-   `enum`: named constants.
-   `ref` (initialized before), `out` (assigned inside).
-   Nullable: `int?`, `string?`.
-   Null operators: `??`, `??=`.

------------------------------------------------------------------------

## Arrays & Indexers

-   1D, 2D (`[,]`), Jagged (`[][]`).
-   Index from end: `^1`, Range: `1..3`.
-   Indexer: `this[int i]` to access object like array.

------------------------------------------------------------------------

## Generics & Collections

-   Generics: type-safe, no boxing.
-   Generic class: `Class<T>`; Generic method: `Method<T>()`.
-   Constraints: `where T : class/struct/new()/Base/IInterface`.
-   Generic collections: `List<T>`, `Dictionary<TKey,TValue>`.
-   Interfaces: `ICollection`, `IList`, `IDictionary`.
-   `foreach`: read-only iteration.
-   Tuples: return multiple values.

------------------------------------------------------------------------

## Delegates & Lambdas

-   Delegate = type-safe method reference.
-   Multicast: `+=` multiple methods.
-   Built-ins: `Action`, `Func`, `Predicate`.
-   Anonymous method: `delegate {}`.
-   Lambda: `(x) => x*x` (used in LINQ).

------------------------------------------------------------------------

## Exceptions & Events

-   C# exceptions are runtime.
-   `try-catch-finally`.
-   Custom exception inherits `Exception`.
-   Events are based on delegates; `+=` subscribe, `?.Invoke()`.

------------------------------------------------------------------------

## LINQ & Language Features

-   LINQ to Objects: query or method syntax.
-   Deferred execution (lazy).
-   Common ops: `Where`, `Select`, `OrderBy`, `Count`, `First`.
-   PLINQ: `AsParallel()`.
-   Anonymous types: `new {}` (read-only).
-   Extension methods: static, `this` first param.
-   Partial class/method: split across files; partial method is void &
    optional.

------------------------------------------------------------------------

## Assemblies & Reflection

-   Assembly = IL + metadata + manifest.
-   Shared assembly: strong name + GAC.
-   Custom attribute: inherit `Attribute`.
-   Reflection: inspect types at runtime.
-   Dynamic load: `Assembly.LoadFrom`.

------------------------------------------------------------------------

## File I/O

-   Streams: `FileStream`, `StreamReader/Writer`.
-   Helpers: `File`, `Directory`, `DriveInfo`.
-   Use `using` for cleanup.

------------------------------------------------------------------------

## Threading & TPL

-   Thread: smallest execution unit.
-   `ThreadStart`, `ParameterizedThreadStart` (single object).
-   ThreadPool: reusable threads.
-   Synchronization: `lock`, `Monitor`, `Interlocked`.
-   `Task` / `Task<T>`: modern async.
-   `async` / `await`: non-blocking.
-   TPL: `Task`, `Parallel.For/ForEach`.

------------------------------------------------------------------------

### Exam Cheatsheet

-   Value vs Reference types.
-   Overload vs Override vs Hide.
-   Interface vs Abstract.
-   `ref` vs `out`.
-   `??`, `??=`.
-   Generic collections \> non-generic.
-   Delegate → Event → Lambda.
-   LINQ is deferred.
-   `lock` prevents race.
-   `Task` + `async/await` for async.
