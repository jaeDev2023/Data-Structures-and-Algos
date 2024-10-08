```javascript
function selectionSort(arr) {
    let n = arr.length;

    for (let i = 0; i < n - 1; i++) {
        // Assume the minimum is the first unsorted element
        let minIndex = i;

        // Find the index of the minimum element in the unsorted portion of the array
        for (let j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }

        // Swap the found minimum element with the first unsorted element
        if (minIndex !== i) {
            [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
        }
    }

    return arr;
}
```
Time complexity: O(n^2) for average and worst cases.
Space Complexity: O(1), as it is an in place sorting algorithm.
