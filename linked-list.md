# Linked List

Linked list is  another linear data structure which stored data maintaining order. Linked list consist of nodes instead of elements\( like Array\) which have two parts.

![](.gitbook/assets/image%20%286%29.png)

In laymen terms each node is consists of a data and a address/value of another node.Hence this data structure allow to store data in discreet manner but maintaining the order at the same time.  Its more dynamic and creates less garbage memory compared to array/dynamic array.

{% hint style="info" %}
Javascript / Typescript are dynamic in nature by default. Read more about  [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).
{% endhint %}

### Node:

```typescript
class LinkedListNode<T> {
    value: (T | null);
    next: (LinkedListNode<T> | null);

    constructor(value: (T | null) = null, next: (LinkedListNode<T> | null) = null) {
        this.value = value;
        this.next = next;
    }
}
```

### Linked List: 

```typescript
class LinkedList<T> {
    private head: (LinkedListNode<T> | null);
    private size: number;

    constructor() {
        this.head = null;
        this.size = 0;
    }
}
```

we will implement below methods for out link list

* append
* prepend
* appendAt
* delete
* search
* utility methods
  * toArray
  * fromArray
  * toString
  * getNodeAtIndex
  * isEmpty

### Append:

```typescript
    append(value: T): void {
        let newNode = new LinkedListNode(value);
        if (this.size === 0) { // linkedlist is empty
            this.head = newNode;
        } else {
            let currentNode = this.head;
            while (currentNode && currentNode.next) {
                currentNode = currentNode.next;
            }
            if (currentNode) currentNode.next = newNode;
        }
        this.size++;
    }
```

### Prepend

```typescript
    prepend(value: T): void {
        let newNode = new LinkedListNode(value);
        if (this.size === 0) { // linkedlist is empty
            this.head = newNode;
        } else {
            let currentHead = this.head;
            this.head = newNode;
            this.head.next = currentHead;
        }
        this.size++;
    }
```

### AppendAt

```typescript
    appendAt(index: number, value: T): void {

        let newNode = new LinkedListNode(value);

        if (this.size === 0) {
            if (index != 0) {
                return;
            } else {
                this.head = newNode;
            }
        }

        if (this.size === 0 && index === 0) {
            newNode.next = this.head;
            this.head = newNode;
            return;
        }

        let current = this.head;
        let previous = null;
        let i = 0;

        while (i < index) {
            previous = current;
            current = current ? current.next : null;

            if (current == null) {
                break;
            }
            i++;
        }

        newNode.next = current;
        if (previous) previous.next = newNode;
    }
```

### Delete

```typescript
   delete(value: T): boolean {
        let deletedItem: boolean = false;
        let currentHead = this.head;

        if(this.head && this.head.value === value) {
            this.head = this.head.next;
            return true;
        }

        while(currentHead && currentHead.next){
            if(currentHead.next.value === value)  {
                deletedItem = true;
                currentHead.next = currentHead.next.next;
                break;
            } else {
                currentHead = currentHead.next;
            }
        }

        return deletedItem;
    }
```

### Search

```typescript
    search(value: T): boolean {
        let itemFound: boolean = false;
        let currentHead = this.head;


        while(currentHead){
            if(currentHead.value === value)  {
                itemFound = true;
                break;
            } else {
                currentHead = currentHead.next;
            }
        }
        return itemFound;
    }
```

### Utils

```typescript
isEmpty(): boolean {
    return this.size === 0;
}


toArray(): T[] {
    let arrayList: T[] = [];

    let currentNode = this.head;
    while (currentNode) {
        if (currentNode.value) arrayList.push(currentNode.value);
        currentNode = currentNode.next;
    }
    return arrayList;
}


fromArray(values: T[]): LinkedList < T > {
    values.forEach(v => this.append(v));
    return this;
}


getNodeAtIndex(index: number): (LinkedListNode < T > | null) {
    let count: number = 0,
        currentHead = this.head,
        resultNode: (LinkedListNode < T > | null) = null;

    while (currentHead) {
        if (index === count) {
            resultNode = currentHead;
            break;
        }
        currentHead = currentHead.next;
        count++;
    }
    return resultNode;
}


toString(joinBy: string = ' '): String {
    return this.toArray().map(s => JSON.stringify(s)).join(joinBy);
}
```

### Final

```typescript

class LinkedListNode<T> {
    value: (T | null);
    next: (LinkedListNode<T> | null);

    constructor(value: (T | null) = null, next: (LinkedListNode<T> | null) = null) {
        this.value = value;
        this.next = next;
    }
}

class LinkedList<T> {
    private head: (LinkedListNode<T> | null);
    private size: number;

    constructor() {
        this.head = null;
        this.size = 0;
    }

    append(value: T): void {
        let newNode = new LinkedListNode(value);
        if (this.size === 0) { // linkedlist is empty
            this.head = newNode;
        } else {
            let currentNode = this.head;
            while (currentNode && currentNode.next) {
                currentNode = currentNode.next;
            }
            if (currentNode) currentNode.next = newNode;
        }
        this.size++;
    }

    prepend(value: T): void {
        let newNode = new LinkedListNode(value);
        if (this.size === 0) { // linkedlist is empty
            this.head = newNode;
        } else {
            let currentHead = this.head;
            this.head = newNode;
            this.head.next = currentHead;
        }
        this.size++;
    }

    appendAt(index: number, value: T): void {

        let newNode = new LinkedListNode(value);

        if (this.size === 0) {
            if (index != 0) {
                return;
            } else {
                this.head = newNode;
            }
        }

        if (this.size === 0 && index === 0) {
            newNode.next = this.head;
            this.head = newNode;
            return;
        }

        let current = this.head;
        let previous = null;
        let i = 0;

        while (i < index) {
            previous = current;
            current = current ? current.next : null;

            if (current == null) {
                break;
            }
            i++;
        }

        newNode.next = current;
        if (previous) previous.next = newNode;
    }

    delete(value: T): boolean {
        let deletedItem: boolean = false;
        let currentHead = this.head;

        if(this.head && this.head.value === value) {
            this.head = this.head.next;
            return true;
        }

        while(currentHead && currentHead.next){
            if(currentHead.next.value === value)  {
                deletedItem = true;
                currentHead.next = currentHead.next.next;
                break;
            } else {
                currentHead = currentHead.next;
            }
        }

        return deletedItem;
    }

    search(value: T): boolean {
        let itemFound: boolean = false;
        let currentHead = this.head;


        while(currentHead){
            if(currentHead.value === value)  {
                itemFound = true;
                break;
            } else {
                currentHead = currentHead.next;
            }
        }
        return itemFound;
    }

    toString(joinBy: string = ' '): String {
        return this.toArray().map(s => JSON.stringify(s)).join(joinBy);
    }

    isEmpty(): boolean {
        return this.size === 0;
    }


    fromArray(values: T[]): LinkedList<T> {
        values.forEach(v => this.append(v));
        return this;
    }

    getNodeAtIndex(index: number): (LinkedListNode<T> | null) {
        let count: number = 0,
            currentHead = this.head,
            resultNode: (LinkedListNode<T> | null) = null;

        while (currentHead) {
            if (index === count) {
                resultNode = currentHead;
                break;
            }
            currentHead = currentHead.next;
            count++;
        }
        return resultNode;
    }

    toArray(): T[] {
        let arrayList: T[] = [];

        let currentNode = this.head;
        while (currentNode) {
            if (currentNode.value) arrayList.push(currentNode.value);
            currentNode = currentNode.next;
        }
        return arrayList;
    }
}

export default LinkedList;
```

