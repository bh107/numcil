# NumCIL [![NumCIL](https://img.shields.io/nuget/dt/NumCIL.svg)](https://www.nuget.org/packages/NumCIL/)
Numeric operations in C# (and VB, IronPyton, F#) 

This project contains the C# implementation of an array programming library, inspired by [Numpy](http://www.numpy.org/).

The library can run in fully managed mode, or transparently switch to direct memory access if the runtime allows it.

To install using Nuget run:
```
PM> Install-Package NumCIL
```

Optionally, you can also install the direct memory manipulation library with `PM> Install-Package NumCIL.Unsafe`.


The performance of the library is generally limited by memory transfer speeds as there is no [loop fusion](https://en.wikipedia.org/wiki/Loop_fusion) implemented, giving performance similar to what can be obtained in NumPy.

The library was originally targeting the [Bohrium runtime system](https://github.com/bh107/bohrium) which has many optimizations, including loop fusion. There exists a support library that will allow [switching a binary to the Bohrium runtime without recompilation](https://github.com/bh107/bohrium/tree/d054603e97276e17e3cfeaf002e6ec600d400868/bridge/cil), but the mapping was not maintained due to lack of resources and demand.

If you want the Bohrium mapping back, please create an issue requesting Bohrium support.
