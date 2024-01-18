# Algorithms

### A fast sorting algorithm with a random reference element for complexity O(n log n)

```const values = [124, 300, 5, 1, 11];

  const defolt = (values) => {
    if (values.length < 2) return values;
    let count = Math.floor(Math.random(3) * values.length);
    let pivot = values[count];
    console.log(one);
    let less = values.slice(1).filter((item) => {
      return item <= pivot;
    });
    console.log(less);
    let more = values.slice(1).filter((item) => {
      return item > pivot;
    });
    console.log(more);
    return defolt(less).concat(pivot, defolt(more));
  };```
