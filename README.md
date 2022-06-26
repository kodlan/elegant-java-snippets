# elegant-java-snippets
Java code snippets

## Table of contents

<details>
<summary>Arrays</summary>

* [`Array initialization`](#Array-initialization)
* [`Fill the array`](#Fill-the-array)
* [`Output the array`](#Output-the-array)
  

</details>

<details>
<summary>Lists</summary>

* [Unmodifiable list initialization](#Unmodifiable-list-initialization)

</details>

<details>
<summary>Sets</summary>


</details>

<details>
<summary>Maps</summary>

* [Unmodifiable map initialization](#Unmodifiable-map-initialization)

</details>

## Arrays

### Array initialization

```java
int[] array = { 1, 2, 3, 4, 5 };
```

<br>[⬆ back to contents](#Table-of-contents)

### Fill the array

```java
int[] array = new int[10];

Arrays.fill(array, 1);     // [1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
Arrays.fill(ar, 1, 5, 2);  // [1, 2, 2, 2, 2, 1, 1, 1, 1, 1]
```

<br>[⬆ back to contents](#Table-of-contents)

### Output the array

```java
System.out.println(Arrays.toString(array));     // int[] for example
System.out.println(Arrays.deepToString(array)); // int[][] for example
```

<br>[⬆ back to contents](#Table-of-contents)

## Lists

### Unmodifiable list initialization

```java
List<Integer> list = Arrays.asList(1, 2, 3);

list = List.of(1, 2, 3);
```

<br>[⬆ back to contents](#Table-of-contents)

## Sets

<br>[⬆ back to contents](#Table-of-contents)

## Maps

### Unmodifiable map initialization

```java
Map<String, String> map = Map.of();

map = Map.of("key", "value");

map = Map.of("key1","value1", "key2", "value2")
    
// ... upto 10 key-value pairs
```
<br>[⬆ back to contents](#Table-of-contents)

## Min Heap, Max Heap, PriorityQueue

<br>[⬆ back to contents](#Table-of-contents)
