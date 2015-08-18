# meda-components
Web Components to aid in interacting with the MeDa Database.

MeDa's (Acronym: MeDa Database) guiding principle is that data about data (AKA: metadata, semantic data, schema, software (we'll go into this later), or as we like to call it: lens) is also data, and as such should be treated the same as any other piece of data.  With that in mind, requests to the MeDa Database have the form:

https://medagae.appspot.com/meda/(lens key)/(target key)

Where (lens key) points to the data that gives the database instructions on how to retrieve the data at the (target key).  You can think of a key as a pointer to all of the data that belongs to a specific scope.  A piece of data belongs to a scope if you only have to store the data in one place if it's stored in that scope.  For instance, if you want to make sure that a string is only 15 characters long, then the appropriate scope for the 15 is in the lens scope for that string.  Also note that you can specify a key pointing to a lens scope in your request, and in fact make lenses that contain data about other lenses.  This delightfully recursive feature is sort of like the mathematical concept of functionals.

The server processes requests by looking at the scope associated with the lens key and first decides what type of data is needed in the request.  There are 9 types of data that the database currently knows how to handle, 4 base types (primitives) and 5 recursive types:
- Base types: Boolean, Key, Number and String
- Recursive types: Condition, Embedded, List, Object and Reference
The base types are pretty self explanatory. If the lens is of type String, then it will have instructions on how to read or write a string in the database.  Here are some detailed descriptions of the recursive types:
- Condition takes data from the target to calculate a consequent sublens.
- Embedded returns data from a different scope that is embedded in the current scope.
- List returns data from a list of embedded scopes.
- Object return data from a list of sublenses
- Reference returns data from a seperate scope that is pointed to with a key from the current scope.  Note, this is a read - only lens.

We are not limitted to putting data that the meda service understands in the lens scopes.  For instance, we can put web components meant for handling the data for a type of lens in an Object lens and use that Object lens with the lens of that type as the target.  If we have a different web component for each type of lens, then we would be able to make a dynamic form for whatever lens is specified in the target.  Of course we aren't limitted to dynamic forms.  We can put all sorts of web components in the database, and use pure data as the glue for the web components instead of frameworks like Angular, etc.

Next steps: improve on this rough drafts.  Put comments in the web components themselves. Make a tutorial.
