# Linked List

_Read this in other languages:_
[_简体中文_](README.zh-CN.md),
[_Русский_](README.ru-RU.md),
[_日本語_](README.ja-JP.md),
[_Português_](README.pt-BR.md),
[_한국어_](README.ko-KR.md),
[_Español_](README.es-ES.md),
[_Turkish_](README.tr-TR.md),
[_Українська_](README.uk-UA.md)

In computer science, a **linked list** is a linear collection
of data elements, in which linear order is not given by
their physical placement in memory. Instead, each
element points to the next. It is a data structure
consisting of a group of nodes which together represent
a sequence. Under the simplest form, each node is
composed of data and a reference (in other words,
a link) to the next node in the sequence. This structure
allows for efficient insertion or removal of elements
from any position in the sequence during iteration.
More complex variants add additional links, allowing
efficient insertion or removal from arbitrary element
references. A drawback of linked lists is that access
time is linear (and difficult to pipeline). Faster
access, such as random access, is not feasible. Arrays
have better cache locality as compared to linked lists.

![Linked List](./images/linked-list.jpeg)

*Made with [okso.app](https://okso.app)*

## Pseudocode for Basic Operations

***
### Insert

```text
Add(value)
  Pre: value is the value to add to the list
  Post: value has been placed at the tail of the list
  n ← node(value)
  if head = ø
    head ← n
    tail ← n
  else
    tail.next ← n
    tail ← n
  end if
end Add
```
```javascript
// Define the Node class
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

// Define the singly linked list class
class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  // Define the Add algorithm
  Add(value) {
    // Create a new node
    let n = new Node(value);
    // If the list is empty, set head and tail to the new node
    if (this.head === null) {
      this.head = n;
      this.tail = n;
    } else {
      // Otherwise, add the new node to the end of the list
      this.tail.next = n;
      this.tail = n;
    }
  }
}

// Create a new instance of the SinglyLinkedList class
let myList = new SinglyLinkedList();

// Add some tasks to the list
myList.Add('Buy groceries');
myList.Add('Finish the project');
myList.Add('Clean the house');

// Now the list contains three tasks, and the tail is pointing to the last task
console.log(myList.tail.value); // Output: "Finish the project"
```
***


```text
Prepend(value)
 Pre: value is the value to add to the list
 Post: value has been placed at the head of the list
 n ← node(value)
 n.next ← head
 head ← n
 if tail = ø
   tail ← n
 end
end Prepend
```
```javascript
// Define the Node class
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

// Define the singly linked list class
class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  // Define the Prepend algorithm
  Prepend(value) {
    // Create a new node
    let n = new Node(value);

    // Set the new node's next pointer to the current head of the list
    n.next = this.head;

    // Set the head of the list to the new node
    this.head = n;

    // If the list was empty, set the tail to the new node as well
    if (this.tail === null) {
      this.tail = n;
    }
  }
}

// Create a new instance of the SinglyLinkedList class
let myFeed = new SinglyLinkedList();

// Add some posts to the feed
myFeed.Prepend('Just had the best coffee ever ☕️');
myFeed.Prepend("Can't wait for the weekend 🎉");
myFeed.Prepend('New year, new me 🥳');

// Now the feed contains three posts, and the head is pointing to the most recent post
console.log(myFeed.head.value); // Output: "New year, new me 🥳"
```
***

### Search

```text
Contains(head, value)
  Pre: head is the head node in the list
       value is the value to search for
  Post: the item is either in the linked list, true; otherwise false
  n ← head
  while n != ø and n.value != value
    n ← n.next
  end while
  if n = ø
    return false
  end if
  return true
end Contains
```

### Delete

```text
Remove(head, value)
  Pre: head is the head node in the list
       value is the value to remove from the list
  Post: value is removed from the list, true, otherwise false
  if head = ø
    return false
  end if
  n ← head
  if n.value = value
    if head = tail
      head ← ø
      tail ← ø
    else
      head ← head.next
    end if
    return true
  end if
  while n.next != ø and n.next.value != value
    n ← n.next
  end while
  if n.next != ø
    if n.next = tail
      tail ← n
      tail.next = null
    else
      n.next ← n.next.next
    end if
    return true
  end if
  return false
end Remove
```

### Traverse

```text
Traverse(head)
  Pre: head is the head node in the list
  Post: the items in the list have been traversed
  n ← head
  while n != ø
    yield n.value
    n ← n.next
  end while
end Traverse
```

### Traverse in Reverse

```text
ReverseTraversal(head, tail)
  Pre: head and tail belong to the same list
  Post: the items in the list have been traversed in reverse order
  if tail != ø
    curr ← tail
    while curr != head
      prev ← head
      while prev.next != curr
        prev ← prev.next
      end while
      yield curr.value
      curr ← prev
    end while
   yield curr.value
  end if
end ReverseTraversal
```

## Complexities

### Time Complexity

| Access    | Search    | Insertion | Deletion  |
| :-------: | :-------: | :-------: | :-------: |
| O(n)      | O(n)      | O(1)      | O(n)      |

### Space Complexity

O(n)

## References

- [Wikipedia](https://en.wikipedia.org/wiki/Linked_list)
- [YouTube](https://www.youtube.com/watch?v=njTh_OwMljA&index=2&t=1s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
