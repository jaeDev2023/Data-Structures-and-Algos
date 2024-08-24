## Knuth-Morris-Pratt Algorithm

## Description
The KMP algorithm is a string-searching algorithm used to find occurences of a pattern in a string.

## Algorithm
```javascript
function computeLPSArray(pattern) {
    const m = pattern.length;
    const lps = new Array(m).fill(0);
    let length = 0;  // Length of the previous longest prefix suffix
    let i = 1;

    while (i < m) {
        if (pattern[i] === pattern[length]) {
            length++;
            lps[i] = length;
            i++;
        } else {
            if (length !== 0) {
                length = lps[length - 1];
            } else {
                lps[i] = 0;
                i++;
            }
        }
    }
    return lps;
}

function KMPSearch(text, pattern) {
    const n = text.length;
    const m = pattern.length;
    const lps = computeLPSArray(pattern);
    let i = 0;  // index for text
    let j = 0;  // index for pattern

    while (i < n) {
        if (pattern[j] === text[i]) {
            i++;
            j++;
        }

        if (j === m) {
            console.log(`Pattern found at index ${i - j}`);
            j = lps[j - 1];
        } else if (i < n && pattern[j] !== text[i]) {
            if (j !== 0) {
                j = lps[j - 1];
            } else {
                i++;
            }
        }
    }
}
```
