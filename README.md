# scala-record

A playspace for Scala macros that implements functionality similar to case classes,
but for `trait`s.

For example, with a record definition called `Complex`:
```scala
@Record
trait Complex {
  def real: Double
  def imag: Double

  def gt(other: Complex): Boolean = abs > other.abs
  def abs: Double = Math.sqrt(real * real + imag * imag)
}
```

We can use generated `apply`, `unapply`, and `toString` methods:
```scala
Complex
Complex(1.0, 2.0)
Complex(1.0, 1.0).abs
Complex.unapply(Complex(1.0, 2.0))
```

Which is printed as:
```text
Complex[real, imag]
Complex[real=1.0, imag=2.0]
1.4142135623730951
Some((1.0,2.0))
```

Initial project setup was adapted from https://github.com/scalamacros/sbt-example-paradise.
