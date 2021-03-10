# Slice and Splice

Slice and Splice are one of the confusing concept related to JavaScript arrays. Many developers got confused with them.

## `Splice`

- Returns the removed items.
- Changes the original array.
- Accepts 3 arguments:
    - Index: required
    - Count: optional – Num of items to be removed from the index. If not given all the items starting from the index
      till the end will be removed.
    - New items to be added: optional

### Uses:

It can be used to remove and add items to an array.

### Examples:

**Remove all items with `Index` argument only-**

```javascript
let arr = [1, 2, 3, 4, 5];
console.log(arr.splice(1));  // [2,3,4,5]
console.log(arr); // [1]
```

**Remove selected items with `Index` and `Count` arguments-**

- If the Count argument-
    - Not provided, then by default all the items would be removed starting from Index argument.
    - Value is less than 0, then no item would be removed and array remains as it is.
    ```javascript
    let arr = [1,2,3,4,5];
    console.log(arr.splice(1, 2));  // [2,3] - two items starting from index 1 would be removed
    console.log(arr); // [1,4,5]
    ```

**Remove selected items and add new items with `Index`, `Count` and `new items` arguments-**

```javascript
let arr = [1, 2, 3, 4, 5];
// two items starting from index 1 would be removed and 3 new items would be added

console.log(arr.splice(1, 2, 6, 7, 8));  // [2,3]
console.log(arr); // [1,6,7,8,4,5]
```

## `Slice`

- Returns the selected items as this method does not remove and changes the original array.
- Does not change the original array.
- 2 arguments
    - Start index: *required* – included
    - End index: *optional* – not included, if not given all the items from start index till the end will be removed.

### Uses:

It can also be used to copy one array to another.

### Examples:

**With `Start index` argument only-**

Returns the selected items starting from start index as and does not change the original array

```javascript
let arr = [1, 2, 3, 4, 5];
console.log(arr.slice(1)); // [2,3,4,5]
console.log(arr); // [1,2,3,4,5]
```

**With `start index` and `end index` arguments-**

`Slice()` will select value starting from start index till end index and value at end index will not be included.

***Positive end index***

```javascript
let arr = [1, 2, 3, 4, 5];
console.log(arr.slice(1, 3)); // [2,3]
console.log(arr); // [1,2,3,4,5]
```

***Negative end index***

If you give a negative end index value, then JS will start counting from the end. In this case, we have provided an end
index = -3

- Value 5 (4th index will be considered as 1 value)
- Value 4 (3rd index will be considered as 2 value)
- Value 3 (2nd index will be considered as 3 value)

So slice method will select value between index 1 and 2, therefore the output is 2.

```javascript
let arr = [1, 2, 3, 4, 5];
console.log(arr.slice(1, -3)); // [2]
console.log(arr); // [1,2,3,4,5]

// Similarly, with (-2) 
let arr = [1, 2, 3, 4, 5];
console.log(arr.slice(1, -2)); // [2,3]
console.log(arr); // [1,2,3,4,5]
```

Now, if you see, the difference between them is not much and they also sound almost the same which in turn increases the
confusion.

## Technique 
You can remember them by their literal meaning.

`Slice` can be defined as a small piece cut from the large portion. So in JS also slice returns the selected items from a
large array.

`Splice` can be defined as a join between two ropes. So in JS, you can use splice to join two arrays at a defined index.

