# Trie class: Prefix Tree

## Trie Node
```javascript
class TrieNode {
  constructor() {
    this.children = {}; // Each node will have a dictionary of children
    this.isEndOfWord = false; // To mark the end of a word
  }
}
```

## Trie Class
```javascript
class Trie {
  constructor() {
    this.root = new TrieNode(); // The root node of the trie
  }

  // Method to insert a word into the Trie
  insert(word) {
    let node = this.root;
    for (let char of word) {
      if (!node.children[char]) {
        node.children[char] = new TrieNode(); // Create a new node if the character doesn't exist
      }
      node = node.children[char];
    }
    node.isEndOfWord = true; // Mark the end of the word
  }

  // Method to search for a word in the Trie
  search(word) {
    let node = this.root;
    for (let char of word) {
      if (!node.children[char]) {
        return false; // If the character isn't found, the word isn't in the trie
      }
      node = node.children[char];
    }
    return node.isEndOfWord; // Check if it's the end of a valid word
  }

  // Method to check if any word in the Trie starts with a given prefix
  startsWith(prefix) {
    let node = this.root;
    for (let char of prefix) {
      if (!node.children[char]) {
        return false; // If the character isn't found, no word with the prefix exists
      }
      node = node.children[char];
    }
    return true; // The prefix exists in the trie
  }
}

```
