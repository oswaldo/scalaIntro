## Scala Introduction
### (Part 1 of N)
<br>
#### Oswaldo Dantas
<br>
#### 2018-03-08

---

## Scala
* Developed at [Ecole polytechnique federale de Lausanne](https://lamp.epfl.ch/) (EPFL)
* [Open Source](https://github.com/scala/scala)
* Released in 2004
* Current Version: 2.12.4
* Statically Typed
* Compilable (JVM or native via LLVM)
* Transpilable (to JavaScript)
* Scriptable (via JSR-223 or [Ammonite](https://github.com/lihaoyi/Ammonite))
* Garbage collected
* Great ecosystem

----

## Tools
* sbt
* Web playgrounds
  * [Scastie](https://scastie.scala-lang.org/)
  * [ScalaFiddle](https://scalafiddle.io/)
* Lots of others depending on your target platform
### The right tool for the job

---

## sbt
* Can run interactivelly
* Can monitor changes (prepending ~ to a command)
  * compile
  * test
  * run
  * install
* Many other commands and tasks
  * natively or through plugins
* End results can be tuned to whatever target you like*

----

## Source code structure
* No mandatory relation between files and packages
* Follow community good practices

---

## Standard library
* Includes core elements like collections, concurrency primitives, io, math
* Interoperability allows accessing target platform libraries

----

## Basic syntax - Packages
* Declaring

```scala
package com.innogames.scalaIntro
```

* Importing

```scala
import com.innogames.scalaIntro._
```

---

## Basic syntax - Values and Variables
```scala
val x = 1
var y = 2
```
* "Everything is an object"
* Type inference
* Byte, Short, Int, Long, Float, Double, Char, String, Boolean, Null, Nothing, Any, AnyVal, AnyRef...
* null is the only value of Null
 * "Calling a function and getting null back is like saying hello and getting a spit in the face as a response"

---

## Basic syntax - Expressions
```scala
val y = if (x > y) x else y
```
* "Everything is an expression"
* No false dichotomy here

---

## Basic syntax - Functions
```scala
def max(x: Int, y: Int): Int = if (x > y) x else y
```
* Return type is optional

---

## Basic syntax - Arguments and Currying
```scala
def currying(x: Int)(y: Int): Int = max(x, y)
val greaterThan2 = currying(2)_
greaterThan2(1) //outputs 2
```

---

## Basic syntax - Traits Classes and Objects
```scala
trait Named { def name: String }
case class Person( val name: String ) extends Named
object VIP extends Named {
  val name = "Chuck Norris"
}
```

---

## Basic syntax - Pattern Matching
```scala
namedElement match {
  case person @ Person(theName) if theName.size < 3 => s"Got a person named $theName. That is short"
  case VIP => throw new RuntimeException("Should never try matching him")
  case _ => println("whatever")
}
```
* "Switch case on steroids"
