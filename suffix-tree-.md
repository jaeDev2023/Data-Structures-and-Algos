# Suffix Tree.
## Description:
The suffix tree allows for efficient searching and analysis through a string.

The tree is composed of nodes and edges. Each edge is a substring. The root is the entire string, 
and each path from root to the leaf is the suffix of the string.

An example of possible suffixes for a word would be:
"Example"
"e", "le", "ple", "mple", "ample", xample", and "example"

## Algorithm:
```javascript
class SuffixTreeNode {
    constructor() {
        this.children = {};  // A map from character to SuffixTreeNode
        this.indexes = [];   // Keeps track of the end indices of the suffixes
    }
}

class SuffixTree {
    constructor() {
        this.root = new SuffixTreeNode();
    }

    // Function to build the suffix tree
    buildTree(text) {
        for (let i = 0; i < text.length; i++) {
            this._insertSuffix(text, i);
        }
    }

    // Function to insert a suffix into the tree
    _insertSuffix(text, startIndex) {
        let currentNode = this.root;
        for (let i = startIndex; i < text.length; i++) {
            let char = text[i];
            if (!currentNode.children[char]) {
                currentNode.children[char] = new SuffixTreeNode();
            }
            currentNode = currentNode.children[char];
            currentNode.indexes.push(startIndex);
        }
    }

    // Function to search for a pattern in the text
    search(pattern) {
        let currentNode = this.root;
        for (let i = 0; i < pattern.length; i++) {
            let char = pattern[i];
            if (!currentNode.children[char]) {
                return [];  // Pattern not found
            }
            currentNode = currentNode.children[char];
        }
        return currentNode.indexes;  // Return the indexes where pattern is found
    }
}
```

## Resources to learn more:
