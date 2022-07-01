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

* [`List initialization`](#List-initialization)
* [`Unmodifiable list initialization`](#Unmodifiable-list-initialization)
* [`List output`](#List-output)

</details>

<details>
<summary>Sets</summary>

* [`Set initialization`](#Set-initialization)
* [`Unmodifiable set initialization`](#Unmodifiable set initialization)

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

### List initialization

Using `add()`:
```java
List<Integer> list = new LinkedList<>() {{
  add(1);
  add(3);
}};
```

Using `Arrays.asList()`:
```java
String[] array = new String[] {"one", "two", "three"};
List<String> list = new ArrayList<>(Arrays.asList(array));  // not for int[] due to cannot infer type arguments for java.util.ArrayList<>

// for int[]:
List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3));
```


<br>[⬆ back to contents](#Table-of-contents)

### Unmodifiable list initialization

```java
List<Integer> list = Arrays.asList(1, 2, 3);

list = Collections.unmodifiableList(Arrays.asList(1, 2, 3));

list = List.of(1, 2, 3);

list = Collections.singletonList(1);

list = Collections.emptyList();
```

<br>[⬆ back to contents](#Table-of-contents)

### List output

```java
System.out.println(list);  // toString()
```

<br>[⬆ back to contents](#Table-of-contents)

## Sets

### Set initialization

Using `add()`:
```java
Set<Integer> set = new HashSet<Integer>() {{
    add(1);
    add(2);
    add(3);
}};
```
Using other collections:
```java
Set<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3));
```
Using `Collections.addAll`:
```java
Set<Integer> mutableSet;
Collections.addAll(mutableSet = new HashSet<>(), 1, 2, 3);
```

<br>[⬆ back to contents](#Table-of-contents)

### Unmodifiable set initialization

```java
Set<Integer> set = Set.of(1, 2, 3);
    
set = Collections.singleton(1);

set = Collections.emptySet();
```

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
