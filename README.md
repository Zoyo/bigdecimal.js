#  BigDecimal for Javascript

*BigDecimal for Javascript* is a pure-Javascript implementation of immutable,
arbitrary-precision, signed decimal numbers. BigDecimal supports **decimal**
math with arbitrary precision.

For a limited time, we will throw in **BigInteger** support at no extra charge!

## Purpose

If this is a problem for you:

    node> 0.1 + 0.2
    0.30000000000000004

Then you need BigDecimal for Javascript. BigDecimal is great for arithmetic of
*financial* information, or anything exceeding the Javascript `Number` (IEEE-754
float) type. Decimal did not make the cut in the new ECMAScript standards so
it&rsquo;s time we got our act together.

## Usage

This software is a [CommonJS][commonjs] module. It is immediately useful in
[NodeJS][node] and [CouchDB][couchdb] projects.

Ready-to-use Javascript builds are available in the tagged Git revisions. Click
the `Download Source` button at the top and choose a `vX.Y` tag. The built code
will be in `build/bigdecimal.js`.

Here is a quick example in NodeJS:

    node> bigdecimal = require("bigdecimal");
    node> i = new bigdecimal.BigInteger("1234567890abcdefghijklmn", 24)
    node> puts("i is " + i)
    i is 60509751690538858612029415201127
    node> d = new bigdecimal.BigDecimal(i)
    node> x = new bigdecimal.BigDecimal("123456.123456789012345678901234567890")
    node> puts("d * x = " + d.multiply(x))
    d * x = 7470299375046812977089832214047022056.555930270554343863089286012030
    node> two = new bigdecimal.BigDecimal('2')
    node> puts("Average = " + d.add(x).divide(two))
    Average = 30254875845269429306014707662291.561728394506172839450617283945
    node> puts("d / x (25 decimal places) = " + d.divide(x, 25,
    ...   bigdecimal.RoundingMode.DOWN()))
    d / x (25 decimal places) = 490131635404200348624039911.8662623025579331926181155

This is exactly like the Java 1.5 `BigInteger` and `BigDecimal` API. See the
[BigDecimal documentation][java_bd] for more information.

If you need an additional format (e.g. browser or NPM), let me know and
hopefully we can add it to the release.

## Implementation

This code is compiled Javascript, originating from the Google [GWT][gwt]
project. GWT version 2.1 supports the Java BigDecimal class. The implementation
came from the Apache Harmony project by way of [gwt-java-math][gwt-java-math]
which optimized it for the Javascript compiler.

Compiled Javascript is a problem; however that is offset by these benefits:

* The implementation is mature, optimized, and maintained by Apache and Google
* The API is well-known, compatible with the J2SE `BigDecimal` and `BigInteger`
  class

If you can&rsquo;t stand the idea of running machine-generated code, please
implement `BigInteger` and `BigDecimal` in native Javascript; convince the world
your implementation is trustworthy, reasonably bug-free, and sure to be
maintained for several years and I will glady include it in this project.

  [gwt]: http://code.google.com/webtoolkit/
  [commonjs]: http://commonjs.org/
  [gwt-java-math]: http://code.google.com/p/gwt-java-math/
  [couchdb]: http://couchdb.apache.org/
  [node]: http://nodejs.org/
  [java_bd]: http://java.sun.com/j2se/1.5.0/docs/api/java/math/BigDecimal.html

## License

BigDecimal for Javascript is licensed under the Apache License, version 2.0.

vim: tw=80
