## learn typescript

#### what is typescript?
- TypeScript is a syntactic superset of JavaScript which adds static typing which means allowing develoepers to add types
- "Syntactic Superset" means that it shares the same base syntax as JavaScript, but adds something to it.
- created by Microsoft
- covert the ts code into vanilla js

#### Why should I use TypeScript?
- Static typing: TypeScript provides static typing, which means that you can specify the types of variables, function parameters, and return types. This can help catch     errors at compile-time rather than run-time, making it easier to debug code.
- IDE support: TypeScript provides better IDE support than JavaScript, including code completion, refactoring, and error highlighting.
- Code maintainability: TypeScript's static typing and interfaces can make your code more maintainable by providing a clear structure and preventing common errors.
- Compatibility with JavaScript: TypeScript is a superset of JavaScript, which means that all valid JavaScript code is also valid TypeScript code. You can gradually       introduce TypeScript into an existing JavaScript project.
- Community support: TypeScript is backed by Microsoft and has a large and active community, which means that there are many resources and libraries available to help     you get started and solve problems.

#### Setup typescript file
I have faced the unauthorized problem, when i have setup the typescript file. The problem error looks like:

tsc : File C:\Users\WALTON\AppData\Roaming\npm\tsc.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170. At line:1 char:1 + tsc types.ts + ~~~ + CategoryInfo : SecurityError: (:) [], PSSecurityException + FullyQualifiedErrorId : UnauthorizedAccess PS E:\learn-typescript>

##### solution:
open the working directory and write the following commands step by step in the terminal

- step 1: set-ExecutionPolicy RemoteSigned -Scope CurrentUser 
- step 2: Get-ExecutionPolicy
- step 3: Get-ExecutionPolicy -list

now we will be able to write typescript code.


##### run single typescript file
terminal: tsc filename(like : tsc script.ts)

#### project setup
terminal: tsc --init

- src---------->typescript files
- output------->typescript javascript converted files
- index.html
- tsconfig.json

here, we have to change something in tsconfig.json file's. <br>
- "rootDir": "./src",
- "outDir": "./output", 

run the code : tsc <br>
run the code with watching file changes : tsc -w


### array
TypeScript has a specific syntax for typing arrays.<br>

1
```
const names : string[] = []
names.push('junaid', 'saber')
console.log(names); // Array [ "junaid", "saber" ]

//we have to put only string in the names array // If we put other data type without string then we will get error
```

2
```
const names : (string | number)[] = []
names.push('junaid', 'saber', 6)
console.log(names);

//we have to put only string and number in the names array
```
3
```
const names : readonly string[] = ['junaid', 'saber']
console.log(names);

//we can't push string, this array is only for read
```




















