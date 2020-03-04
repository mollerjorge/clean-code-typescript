# Variables: Meaningful Names

### Use intention revealing names

Names should reveal intent, meaning that if we need to add a comment to explain what a variable holds then we are not choosing the right name.

_**BAD**_

```typescript
interface Cell {
    value: string
    status: number
}
    
function getThem(list: Cell[]): Cell[] {
    const list1: Cell[] = [];
    for (let i: number = 0; i < list.length; i ++) {
        if (list[i].status === 4) {
            list1.push(list[i]);
        }
    }
    return list1;
}
```

_**GOOD**_

```typescript
interface Cell {
    value: string
    status: number
}

const FLAGGED = 4;
    
function getFlaggedList(list: Cell[]): Cell[] {
    const flaggedListRet: Cell[] = [];
    for (let i: number = 0; i < list.length; i ++) {
        if (list[i].status === FLAGGED) {
            flaggedListRet.push(list[i]);
        }
    }
    return flaggedListRet;
}
```

_**EVEN BETTER**_

```typescript
interface Cell {
    value: string
    status: number
    isFlagged(): boolean
}

const FLAGGED = 4;
    
function getFlaggedList(list: Cell[]): Cell[] {
    const flaggedListRet: Cell[] = [];
    for (let i: number = 0; i < list.length; i ++) {
        if (list[i].isFlagged()) {
            flaggedListRet.push(list[i]);
        }
    }
    return flaggedListRet;
}
```

### Use Pronounceable Names

_**BAD**_

```javascript
class DtaRcrd102 {
    private genmdhms: Date;
    private modymdhms: Date;
    private pszqint: string;
    /**/
}
```

_**Good**_

```typescript
class Customer {
    private generationTimestamps: Date;
    private modificationTimestamp: Date;
    private recordId: string = "102"
}
```

### Use searchable names

_**BAD**_

```typescript
for (let i: number = 0; i < 5; i ++) {
    // Do something
}
```

_**GOOD**_

```typescript
const WORK_DAYS_PER_WEEK = 5;

for (let i:number = 0; i < WORK_DAYS_PER_WEEK; i++) {
    // Do something
}
```

### Interfaces and Implementations

Instead of pre-fixing the interfaces with an `I` use `IMPL` in the class that is going to implement the interface

_**BAD**_

```typescript
interface IEmployeeFactory {
    makeEmployee(type: string): Employee
}

class EmployeeFactory implements IEmployeeFactory {
    /*some implementation*/
}
```

_**GOOD**_

```typescript
interface EmployeeFactory {
    makeEmployee(type: string): Employee
}

class EmployeeFactoryImpl implements EmployeeFactory {
    /*some implementation*/
}
```

### Avoid Mental Mapping

Avoid single letter names for variables unless you are writing a loop counter. In most contexts a single-letter name is poor choice, it's just a placeholder that the reader has to mentally map to an actual concept.

A quote I really liked from this section is: 

> One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand.

### Class Names

Classes and object should have noun or noun phrase names like `Customer` , `WikiPage`, `Account` and `AddressParser` . Avoid words like `Manager` , `Processor` or `Info` in the name of a class. A class name should not be a verb.

### Method Names

Methods and Functions should have verb or verb phrase names like `postPayment` , `dletePage` , or `save`. Accessors, mutators, and predicates should be named for their value and prefixed with `get`, `set`, and `is` .

### Pick one word per concept

This basically means to pick one word per abstract concept and \*stick to it\*

