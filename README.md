# Algorithms

### Binary search algorithm of complexity O(log n)

searches for the desired value in the sorted array by dividing the array in half

```
const binarySearch = (arr, target) => {
    let left = 0;
    let right = arr.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) {
            return mid; 
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return -1; // Элемент не найден
}
```

### A fast sorting algorithm with a random reference element for complexity O(n log n)

Sorts the array by dividing it in half using a checkpoint, in order to avoid the worst number of operations performed, it is recommended to set a random checkpoint, otherwise the complexity of the algorithm may change from O(n log n) to O(n2), although there is a small chance, but it is better to avoid this

```
  const values = [124, 300, 5, 1, 11];

  const sorting = (values) => {
    if (values.length < 2) return values;
    let count = Math.floor(Math.random(3) * values.length);
    let pivot = values[count];
    
    let less = values.slice(1).filter((item) => {
      return item <= pivot;
    });

    let more = values.slice(1).filter((item) => {
      return item > pivot;
    });

    return sorting(less).concat(pivot, sorting(more));
  };
```
