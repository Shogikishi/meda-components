# meda-components
Web Components to aid in interacting with the MeDa Database.
[Tutorial](//github.com/thanacles/meda-components/wiki)

MeDa's (Acronym for MeDa Database) guiding principle is that data about data (AKA: metadata, semantic data, schema, or as we like to call it: lens) is also data, and as such should be treated the same as any other piece of data.  With that in mind, all of the data is stored in an unstructured data lake and requests to the MeDa Database have the form:

https://medagae.appspot.com/meda/[lens key]/[target key]

Where [lens key] points to the data that gives the database instructions on how to retrieve the data at the [target key].  You can think of a key as a pointer to all of the data that belongs to a specific scope.  A piece of data belongs to a scope if you only have to store the data in one place if it's stored in that scope.  For instance, if you want to make sure that a string is only 15 characters long, then the appropriate scope for the number 15 is in the lens scope for that string.  One benefit to this approach, is that lens data is fully recursive.  We could make lenses only meant for other lenses, in that case the target key would point to a lens scope.

The MeDa environent makes it easy to make self sustaining loosely coupled components of code to process its data.  There are 9 components that the server uses and you can build any number of web components on top of that.  The 9 server components are:
- Base types: Boolean, Key, Number and String
- Recursive types: Condition, Embedded, List, Object and Reference
The base types are pretty self explanatory. If the lens is of type String, then it will have instructions on how to read or write a string in the database.  Here are some detailed descriptions of the recursive types:
- Condition takes data from the target to calculate a consequent sublens.
- Embedded returns data from a different scope that is embedded in the current scope.
- List returns data from a list of embedded scopes.
- Object return data from a list of sublenses
- Reference returns data from a seperate scope that is pointed to with a key from the current scope.  Note, this is a read - only lens.

In a web development frame of reference, Web Components make up basic units of functionality and pure data is used as the glue to bring web components together.
