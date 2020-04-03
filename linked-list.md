# Linked List

Linked list is  another linear data structure which stored data maintaining order. Linked list consist of nodes instead of elements\( like Array\) which have two parts.

![](.gitbook/assets/image%20%286%29.png)

In laymen terms each node is consists of a data and a address/value of another node.Hence this data structure allow to store data in discreet manner but maintaining the order at the same time.  Its more dynamic and creates less garbage memory compared to array/dynamic array.

{% hint style="warning" %}
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

### Linked List 

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



