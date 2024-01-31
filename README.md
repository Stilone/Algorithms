# Algorithms

### Binary search algorithm of complexity O(log n):

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
#
### A fast sorting algorithm with a random reference element for complexity O(n log n):

Sorts the array by dividing it in half using a checkpoint, in order to avoid the worst number of operations performed, it is recommended to set a random checkpoint, otherwise the complexity of the algorithm may change from O(n log n) to O(n2), although there is a small chance, but it is better to avoid this

```
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
#
### An example of a breadth-first search algorithm using graphs

In a breadth-first search algorithm, it is important to check areas first 1, then 2. Also, a breadth-first search helps to determine whether there is a path and A to B. If you need to find the shortest X in a problem, then you need to model the problem with a graph and use a breadth-first search to solve it

```
const graph = {};
graph["you"] = ["alice", "bob", "claire"];
graph["bob"] = ["anuj", "peggy"];
graph["alice"] = ["peggy"];
graph["claire"] = ["thom", "jonny"];
graph["anuj"] = [];
graph["peggy"] = [];
graph["thom"] = [];
graph["jonny"] = [];

/**
 * Determine whether a person is a seller
 * @param {string} name Friend's name
 * @returns {boolean} Result of checking
 */
function personIsSeller(name) {
  return name[name.length - 1] === "m";
}

/**
 * Find a mango seller
 * @param {string} name Friend's name
 * @returns {boolean} Search results
 */
function search(name) {
  let search_queue = [];
  search_queue = search_queue.concat(graph[name]);
  // This array is how you keep track of which people you've searched before.
  const searched = [];
  while (search_queue.length) {
    let person = search_queue.shift();
    // Only search this person if you haven't already searched them
    if (searched.indexOf(person) === -1) {
      if (personIsSeller(person)) {
        console.log(person + " is a mango seller!");
        return true;
      }

      search_queue = search_queue.concat(graph[person]);
      // Marks this person as searched
      searched.push(person);
    }
  }
  return false;
}

search("you"); // thom is a mango seller!
```
