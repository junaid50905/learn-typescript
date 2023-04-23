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

### data type
there are three data types in ts
- number: all types  of number like: integer, float, positive, negative
- string
- boolean
- any
- object
- void

### variable
```
const studentName : string = 'junaid'
const studentRoll : number = 21

console.log(`name: ${studentName} --- roll: ${studentRoll}`); //name: junaid --- roll: 21
```

```
let a = 3
console.log(a);
a= "string" // here we will get an error . karon amra upore variable declareation er sathe value assign kore dici, ar tokhon variable er implicit data type sihebe number hoye geche
console.log(a);
```
###### any: a spicial data type
```
let a :any = 3
console.log(a);
a= "string" // ekhon ar error pabo nah, karon amra bole diyechi any type of data we can put
console.log(a);
```

### array
TypeScript has a specific syntax for typing arrays.<br>

-1
```
const arr = [1,4]
// ei array te integer ar flot chara ono kono data type er value push korte nah
```

-1
```
const arr = [1, "junaid"]
// ei array te integer/flot and string chara ono kono data type er value push korte nah// we will get an error when we will want to push boolean value
```

-1
```
const arr = [1, "junaid", false]
// ei array te integer/flot, string, boolean value push korte parbo
```

0
```
const values = []
// in this array we can put any types of value

values.push('junaid')
console.log(values); // Array [ "junaid" ]
values.push(54)
console.log(values); // Array [ "junaid", 54 ]
values.push(true)
console.log(values); // Array [ "junaid", 54, true ]
```

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




### object

1
```
let person = {
    name: 'junaid',
    age: 32,
    isActive: false,
}

person.country = 'Bangladesh' //getting error // we will not be able to add country. karon amara jokhon person name ekti object toiri korechi tokho name=string, age=number ar isActive=boolean cara onno property add korte parbo nah. ebong name, age, isActive er data type change o korte parbo nah.
```

2
```
let person: object

person={
    name: "junaid",
    age: 32,
    isMarried : false
}

// eikhane amra person variable ke object data type diye set kore diyechi, kintu amara object er property gulo set kore dei nai, tai amra caile je kono property rakhte parbo
```


3
```
let person : {
    name: string,
    age: number,
    isMarried: boolean,
}
//eikhane amra person object er structure ta set kore diyeci, ei structure er bahire jodi kew value rakhe ba notun kono property add korar try kore then error dekhabe.
```

jemon
```
let person : {
    name: string,
    age: number,
    isMarried: boolean,
}

person={
    name: 'junaid',
    age: 32,
    isMarried: false
}

or,
const car: { type: string, model: string, year: number } = {
    type: "Toyota",
    model: "Corolla",
    year: 2009
};
here, is everything good // amra caileo eikhane property missing rakhte parbo nah. mane, dori year dilam nah, tahole amra eikhane error pabo. ar ei problem dur korar jonno ache optional property. nicher 4 e example deya holo
```

4 / optional property
```
const car: { type: string, model: string, year?: number } = {
    type: "Toyota",
    model: "Corolla",
};

// ekhon caile amara year na o rakhte pari.
```



5
```
let person : object

person = ['junaid', 22] // eikhane kono error asbe nah karon, array is one kind of onbject in js
```




### function
1/ void

this is the default return type of a function<br>
The type void can be used to indicate a function doesn't return any value.
```
function myFun() :void {
    console.log('hi there');
}
myFun()
```

or default
```
function myFun() {
    console.log('hi there');
}
myFun()
```

2/ return type

this function will return a number
```
function myFun() : number{
    return 4 + 5;
}
console.log(myFun());
```

for arrow function
```
const less = (b : string) : string=> {
    return `hi, ${b}`
}
console.log(less('arman'));
```



3/ parameters
```
function myFun(a: string, b: number) {
    console.log(`My name is ${a} and age is ${b}`);
    
}
myFun("junaid", 23)
```

4/ Optional Parameters
```
function add(a: number, b: number, c?: number) {
    return a + b + (c || 0) //8
}
console.log(add(3,5));
```

5/Default Parameters
```
function add(a: number, b: number, c: number = 10) {
    return a + b + (c || 0)
}
console.log(add(3,5));

```

6/ named parameter

```
function add({a , b}: {a:number, b:number}){
    return a + b
}
console.log(add({a: 3, b:5})); //8

```
7/ rest parameters

8/ type alias

type alias er madhomme amra type gulo ke seperately alada kore pelte pari, pore caile amra jekono jaygay ei type gulo ke use korte pari

###### example: one

without alias
```
let id: string | number = 23
```
eitake amra type alias er madhomme nicher moto kore likhte pari

with alias
```
type idType = string | number

let id: idType = 23
```
amra caile ei idType ke jekono jaygay use korte pari.


##### example: two

without alias
```
const userDetailed = (user: { id: string | number, name: string, age: number, datheOFBirth: string }) => {
    console.log(`Hello, ${user.name} your age is ${user.age} and date of birth is ${user.datheOFBirth}, use this id ${user.id}`);
}
userDetailed({ id: 12, name: 'junaid', age: 23, datheOFBirth: '18-april-1999' })
```

with alias
```
type idType = string | number
type userDetailedType = { id: idType, name: string, age: number, datheOFBirth: string }

const userDetailed = (user: userDetailedType) => {
    console.log(`Hello, ${user.name} your age is ${user.age} and date of birth is ${user.datheOFBirth}, use this id ${user.id}`);
}
userDetailed({ id: 12, name: 'junaid', age: 23, datheOFBirth: '18-april-1999' })

```


### function signature
function signature bolte bujay je ekti function er structure ta kemon hobe ta.

##### example: one

```
// ekjon developer caile add nam a ekti function banate parbe but function er structure ta hote hobe ei rokom
let add : (a: number, b:number)=> number

// we may change the parameter name // 
add = (firstNumber: number, secondNumber: number) =>{
    return firstNumber + secondNumber;
}

console.log(add(7, 4));

```



















