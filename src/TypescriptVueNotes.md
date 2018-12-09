*Miscellanous notes about Typescript and using Vue with Typescript*

Most popular ways of writing Vue components with Typescript

- Vue class component: Typescript decorator that provides ability to
  write class-style components. It is usually used in conjunction with
  vue-property-decorator. Vue-class-component is officially maintained
  by Vue core team.
- Vue.extend() - lets Typescript infer types inside Vue component
  options.

Typerscipt

- != Non null assertion operator. Means that expression cannot be null
  or undefined.
- Void = absence of having any type at all. For example, it is often
  used as the return type of functions that do not return a value.
- Interface = way to create complex data types
- Way to delclare an array of given types (ex. String) = String[ ]
- Variables declared wiht 'let' that are changed inside the block
  statement remaine unchanged outside the block statement
- ? after variable = optional parameter
- 'Static' before prop / method inside classes = means that the class /
  method is visible on the class itself rather than the instances
- To access static field - precede it with the name of the class
- Super -> When creating a class that extends another class super calls
  constructor on the 'parent' class
- Instanceof - a way to check whether the given object was creating
  extending the given class
