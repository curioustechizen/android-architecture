# UPDATE

There is already [another fork](https://github.com/aballano/android-architecture/tree/dev-todo-mvp-kotlin) that has converted this project to Kotlin, and that fork has gone even further (added Kotlin Android extensions, created some extension functions etc). I don't expect to continue work on my fork.

# dev-todo-mvp-kotlin

This project aims to convert the [todo-mvp](https://github.com/googlesamples/android-architecture/tree/todo-mvp) branch to idiomatic Kotlin, while also not being a complete rewrite.

### Approach

I started off by using Android Studio's "Convert Java File to Kotlin" to convert each significant file to Kotlin. This generates code that is not necessarily idiomatic. I then tried to make each converted file idiomatic. For example:

  - Use kotlin properties and initialize them in constructor where appropriate. In most cases this eliminates the need to separate constructor parameters that are assigned to member variables
  - Use `apply{}` liberally wherever multiple methods have to be called on the same object in quick succession
  - Take advantage of Kotlin's nullable types and null-safe method calls to reduce the number of `if(null)` checks
  - Use `lateinit val` liberally, especially in Fragments and Activities for "final" properties that will be set only once (in `onCreate` for example) but cannot be set in the constructor
  - Used string templates instead of concatenation (in a few places)
  - Used if-expressions to make some code more concise

### TODO

Of course, the project is still far far from idiomatic Kotlin. Even without doing a complete re-write there are still several things that can be improved.

  - [ ] Get rid of the hideous `!!` operator sprinkled all over
  - [ ] Functional programming: Several places in the code can benefit from higher order functions instead of interfaces
  - [ ] Convert tests to Kotlin
  - [ ] Several instances of using statics or singletons need to be revisited to make them Kotlinesque
