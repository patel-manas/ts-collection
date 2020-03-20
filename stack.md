---
description: implementation of stack with typescript
---

# Stack

creating  a class Stack with two property items and size. 

```text
export default class Stack<T> {

    private items: T[];
    private size: number;

    constructor() {
        this.items = [];
        this.size = 0;
    }
}


```

we are going to add below methods for the stack:

* push
* pop
* peek
* delete
* search

### Push

```text
    push (value: T): void {
        this.items[this.size] = value;
        this.size++;
    }
```

### Pop

```text
    pop(): (T | undefined) {
        if(this.size > 0) {
            return this.delete(this.size - 1);
        } else {
            this.items[this.size];
        }
    }
```

### Delete

```text
    delete(index: number): (T | undefined) {
        let items: T[] = [];
        let deletedItem = this.items[index] || undefined;
        if(!deletedItem) {
            return deletedItem;
        }
        for(let i = 0; i < this.size; i++) {
           
            if( i >= index ){
                if(this.items[i + 1]) {
                    items[i] = this.items[i + 1];
                }
            } else {
                items[i] = this.items[i];
            }
        }
        this.items = items;
        this.size--;
        return deletedItem;
    }
```

### Search

```text
    search(value: T): Boolean {
        let isPresent = false;
        for(let i = 0; i < this.size; i++) {
            if(this.items[i] === value) {
                isPresent = true;
                break;
            }
        }
        return isPresent;
    }
```

### IsEmpty

```text
    isEmpty(){
        return this.size === 0;
    }
```

### ToString

```text
    toString(joinBy: string = ' '): string {
        return this.items.join(joinBy);
    }
```

### Final

```text
export default class Stack<T> {

    private items: T[];
    private size: number;

    constructor() {
        this.items = [];
        this.size = 0;
    }

    push (value: T): void {
        this.items[this.size] = value;
        this.size++;
    }

    pop(): (T | undefined) {
        if(this.size > 0) {
            return this.delete(this.size - 1);
        } else {
            this.items[this.size];
        }
    }

    delete(index: number): (T | undefined) {
        let items: T[] = [];
        let deletedItem = this.items[index] || undefined;
        if(!deletedItem) {
            return deletedItem;
        }
        for(let i = 0; i < this.size; i++) {
           
            if( i >= index ){
                if(this.items[i + 1]) {
                    items[i] = this.items[i + 1];
                }
            } else {
                items[i] = this.items[i];
            }
        }
        this.items = items;
        this.size--;
        return deletedItem;
    }

    isEmpty(){
        return this.size === 0;
    }

    search(value: T): Boolean {
        let isPresent = false;
        for(let i = 0; i < this.size; i++) {
            if(this.items[i] === value) {
                isPresent = true;
                break;
            }
        }
        return isPresent;
    }
    
    toString(joinBy: string = ' '): string {
        return this.items.join(joinBy);
    }
}


```

### Usage

```text
let stackInstance = new Stack();

// add values
stackInstance(
```

{% embed url="https://stackblitz.com/edit/typescript-2fh48o?ctl=1&embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor" %}



