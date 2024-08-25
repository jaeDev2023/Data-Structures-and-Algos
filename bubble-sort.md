'''javascript
function bubbleSort(arr) {
    let n = arr.length;
    let swapped;

    // Repeat the process until no swaps are made
    do {
        swapped = false;

        // Traverse the array, and swap elements if they are in the wrong order
        for (let i = 0; i < n - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                // Swap arr[i] and arr[i + 1]
                [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]];
                swapped = true;
            }
        }
        // Reduce the length for each pass as the largest elements are already sorted
        n--;
    } while (swapped);

    return arr;
}
'''

Time Complexity: O(n^2)
Space Complexity: O(1)
