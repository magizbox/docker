# Scala

![](http://ncredinburgh.com/img/blog/henry_coles/scala-logo.gif)

<blockquote>
  Scala is a programming language for general software applications. Scala has full support for functional programming and a very strong static type system. This allows programs written in Scala to be very concise and thus smaller in size than other general-purpose programming languages. Many of Scala's design decisions were inspired by criticism of the shortcomings of Java.
</blockquote>

<h3>Tools</h3>

<table>
<tbody>
<tr>
<td style="text-align:center;width:50%;"><img src="https://cdn2.iconfinder.com/data/icons/ballicons-2-free/100/wrench-32.png" alt="" />
Build Tool</td>
</tr>
<tr>
<td style="text-align:center;"><a href="http://www.scala-sbt.org/" target="_blank">SBT</a></td>
</tr>
</tbody>
</table>

<a href="https://confluence.jetbrains.com/display/SCA/Scala+Plugin+for+IntelliJ+IDEA">Creating and Running Your Scala Application</a>
<a href="https://docs.sigmoidanalytics.com/index.php/Step_by_Step_instructions_on_how_to_build_Spark_App_with_IntelliJ_IDEA">Step by Step instructions on how to build Spark App with IntelliJ IDEA</a>

# Scala: Syntax

## Convention [^1]

### Keep It Simple

### Don't pack two much in one expression

```scala
/*
 * It's amazing what you can get done in a single statement
 * But that does not mean you have to do it.
 */
jp.getRawClasspath.filter(
  _.getEntryKind == IClasspathEntry.CPE_SOURCE).
  iterator.flatMap(entry =>
    flatten(ResourcesPlugin.getWorkspace.
      getRoot.findMember(entry.getPath)))
```

#### Refactor

* There's a lot of value in meaningfull names.
* Easy to add them using inline vals and defs

```scala
val sources = jp.getRawClasspath.filter(
  _.getEntryKind == IClasspathEntry.CPE_SOURCE)
def workspaceRoot =
  ResourcesPlugin.getWorkspace.getRoot
def filesOfEntry(entry: Set[File]) =
  flatten(worspaceRoot.findMember(entry.getPath)
sources.iterator flatMap filesOfEntry
```

### Prefer Functional

By default

- use vals, not vars
- use recursions or combinators, not loops
- use immutable collections
- concentrate on transformations, not CRUD

When to deviate from the default
- sometimes, mutable gives better performance.
- sometimes (but not that often!) it adds convenience

### But don't diablolize local state

Why does mutable state lead to complexity?

It interacts with different program parts in ways that are hard to track.

=> Local state is less harmful than global state.

### "Var" Shortcuts

```scala
var interfaces = parseClassHeader()...
if (isAnnotation) interfaces += ClassFileAnnotation
```

**Refactor**

```scala
val parsedIfaces = parseClassHeader()
val interfaces =
  if (isAnnotation) parsedIfaces + ClassFileAnnotation
  else parsedIfaces
```

[^1]: [Martin Odersky - Scala with Style](https://www.youtube.com/watch?v=kkTFx3-duc8)

# Scala: Data Structure

## Scala: Collection

# Scala: IDE

# IntellIJ: Scala IDE

# Online IDE

[http://www.tryscala.com/](http://www.tryscala.com/)
