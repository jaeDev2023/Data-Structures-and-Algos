# Linked List


```javascript
// Node class: Represents each element in the linked list
class Node {
    constructor(value) {
        this.value = value;   // The value or data stored in the node
        this.next = null;     // Pointer to the next node in the list
    }
}

// LinkedList class: Manages the linked list
class LinkedList {
    constructor() {
        this.head = null;    // Pointer to the first node in the list
        this.size = 0;       // Size of the linked list
    }

    // Add a node to the end of the list
    append(value) {
        const newNode = new Node(value);

        // If the list is empty, make the new node the head
        if (this.head === null) {
            this.head = newNode;
        } else {
            let current = this.head;

            // Traverse the list to find the last node
            while (current.next !== null) {
                current = current.next;
            }

            // Set the next pointer of the last node to the new node
            current.next = newNode;
        }

        this.size++;
    }

    // Add a node to the beginning of the list
    prepend(value) {
        const newNode = new Node(value);
        
        // Point the new node's next to the current head
        newNode.next = this.head;
        
        // Make the new node the new head
        this.head = newNode;

        this.size++;
    }

    // Remove a node by value
    remove(value) {
        if (!this.head) return null;

        // If the node to remove is the head
        if (this.head.value === value) {
            this.head = this.head.next;
            this.size--;
            return;
        }

        let current = this.head;
        let previous = null;

        // Traverse the list to find the node to remove
        while (current !== null && current.value !== value) {
            previous = current;
            current = current.next;
        }

        // If the node was found, remove it by adjusting the pointers
        if (current !== null) {
            previous.next = current.next;
            this.size--;
        }
    }

    // Find a node by value
    find(value) {
        let current = this.head;

        // Traverse the list to find the node
        while (current !== null) {
            if (current.value === value) {
                return current;
            }
            current = current.next;
        }

        // Return null if the node is not found
        return null;
    }

    // Print the entire list (for debugging purposes)
    printList() {
        let current = this.head;
        let result = "";

        while (current !== null) {
            result += current.value + " -> ";
            current = current.next;
        }

        console.log(result + "null");
    }

    // Get the size of the list
    getSize() {
        return this.size;
    }
}
```
