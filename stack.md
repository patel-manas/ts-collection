# Stack / Array

Stack and Array both follow LIFO \( Last in first out \).  Only in Stack basic operation is involved i:e:- operation with the element in the top of the stack ,  here the below code demonstration  includes both operation for an array and  stack.

{% hint style="info" %}
The **`shift`** and **`unshift`** method violates the LIFO methodology, but knowingly ignored them as the main aim is to understand data structure.
{% endhint %}

creating  a class Stack with two property items and size. 

```typescript
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

* push \(Array and Stack\)
* pop \(Array and Stack\)
* peek \(Stack\)
* delete \(Array\) 
* search \(Array\)
* isEmpty \(Array\)

### Push

Push is a method where we can add an item to the stack/array. It will add the item in the top of the stack / end of an array.

```typescript
    push (value: T): void {
        this.items[this.size] = value;
        this.size++;
    }
```

### Pop

this method removes the element from the top of the stack / end of .the array. 

```typescript
    pop(): (T | undefined) {
        if(this.size > 0) {
            return this.delete(this.size - 1);
        } else {
            this.items[this.size];
        }
    }
```

### Delete

This method is for Array operation which is widely required in practical usage. Delete method removes an item from a specific index from the Array. It returns the deleted item or undefined if the specified index is out of range.

```typescript
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

This method traverses the array and returns true or false base on the availability of the specified item in the Array.

```typescript
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

This method is simply to check whether the stack/Array contains any item or not.

```typescript
    isEmpty(){
        return this.size === 0;
    }
```

### ToString

ToString is a utility method which helps to visualising the stack/array. By default the items are returned separated by a string but it also has a provision of custom separator can be passed as an argument.

```typescript
    toString(joinBy: string = ' '): string {
        return this.items.join(joinBy);
    }
```

### Final

After combining what we learned above: 

```typescript
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

{% embed url="https://stackblitz.com/edit/typescript-2fh48o?ctl=1&embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor" %}



