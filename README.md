mongo-fsharp-driver-prototype
=============================

Make using MongoDB from F# more natural by defining new operators that
are more idiomatic to the language.

Ideas for more convenient query writing
---------------------------------------

  - curried query builder for use with `|>` operator
  - type provider for `database`.`collection`.`field`... access
  - code quotations for succinct expressions, e.g. `<`, `>`, `=`
  - extend computation expressions for defining queries, e.g. `unwind`

### Structure of the type provider

Lives in the namespace `FSharp.MongoDB.Driver.TypeProvider`.

Need to redefine the `MongoConnection` to accept settings via type
parameters, similar to the `SqlDataConnection` module.

Connects to the server and provides a static method `GetDataContext()`
that returns a `MongoServer` type. In addition, the data context also
provides instance properties erased as `MongoDatabase` types with names
as those available from the server.

These wrapped types will also provide additional instance properties
erased as `MongoCollection` types with names as those contained in the
database.

Probably employ a similar strategy for the documents themselves.
