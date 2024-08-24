# Rabin Karp
## Description
This algorithm is used to find patterns within a string

```javascript
function rabinKarp(text, pattern) {
    const base = 256; // Number of characters in the input alphabet (ASCII)
    const prime = 101; // A prime number to mod the hash values
    const n = text.length;
    const m = pattern.length;
    let patternHash = 0; // Hash value for the pattern
    let textHash = 0; // Hash value for the text
    let h = 1; // The value of base^(m-1)

    // Calculate h = base^(m-1) % prime
    for (let i = 0; i < m - 1; i++) {
        h = (h * base) % prime;
    }

    // Calculate the hash value of the pattern and the first window of text
    for (let i = 0; i < m; i++) {
        patternHash = (base * patternHash + pattern.charCodeAt(i)) % prime;
        textHash = (base * textHash + text.charCodeAt(i)) % prime;
    }

    // Slide the pattern over the text one by one
    for (let i = 0; i <= n - m; i++) {
        // Check if the hash values of the current window of text and pattern match
        if (patternHash === textHash) {
            // Check for characters one by one to avoid false positives
            let match = true;
            for (let j = 0; j < m; j++) {
                if (text[i + j] !== pattern[j]) {
                    match = false;
                    break;
                }
            }
            if (match) {
                console.log(`Pattern found at index ${i}`);
            }
        }

        // Calculate hash value for the next window of text
        if (i < n - m) {
            textHash = (base * (textHash - text.charCodeAt(i) * h) + text.charCodeAt(i + m)) % prime;

            // Convert negative hash value to positive
            if (textHash < 0) {
                textHash += prime;
            }
        }
    }
}
```
