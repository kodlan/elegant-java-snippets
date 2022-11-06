# elegant-java-snippets
Java code snippets

## Table of contents

<details>
<summary><b>🔢 Arrays</b></summary>

* [`Array initialization`](#Array-initialization)
* [`Fill the array`](#Fill-the-array)
* [`Output the array`](#Output-the-array)
* [`Sort the array`](#Sort-the-array)
* [`Concatenate two arrays`](#Concatenate-two-arrays)

&nbsp;&nbsp;&nbsp;[Initializa a stream](#stream-initialization) and then:
* [`Check if all elements are equal`](#Check-if-all-elements-are-equal)
* [`Find maximum integer from the stream`](#Find-maximum-integer-from-the-stream)
* [`Count occurrences of some number in a stream`](#Count-occurrences-of-some-number-in-a-stream)
* [`Get distinct values`](#Get-distinct-values)

</details>

<details>
<summary><b>🍱 Sets</b></summary>

* [`Set initialization`](#Set-initialization)
* [`Unmodifiable set initialization`](#Unmodifiable-set-initialization)

&nbsp;&nbsp;&nbsp;Common for collections:
* [`Min, max element`](#min-max-elements)

&nbsp;&nbsp;&nbsp;[Initializa a stream](#stream-initialization) and then:
* [`Check if all elements are equal`](#Check-if-all-elements-are-equal)
* [`Find maximum integer from the stream`](#Find-maximum-integer-from-the-stream)
* [`Count occurrences of some number in a stream`](#Count-occurrences-of-some-number-in-a-stream)

</details>

<details>
<summary><b>🗂 Lists</b></summary>

* [`List initialization`](#List-initialization)
* [`Unmodifiable list initialization`](#Unmodifiable-list-initialization)
* [`List output`](#List-output)
* [`List sort`](#List-sort)
* [`Binary search`](#Binary-search)
* [`Reverse list`](#Reverse-list)
* [`Rotate list`](#Rotate-list)

&nbsp;&nbsp;&nbsp;Common for collections:
* [`Min, max element`](#min-max-elements)

&nbsp;&nbsp;&nbsp;[Initializa a stream](#stream-initialization) and then:
* [`Check if all elements are equal`](#Check-if-all-elements-are-equal)
* [`Find maximum integer from the stream`](#Find-maximum-integer-from-the-stream)
* [`Count occurrences of some number in a stream`](#Count-occurrences-of-some-number-in-a-stream)
* [`Get distinct values`](#Get-distinct-values)

</details>

<details>
<summary><b>📦 Collections</b></summary>

* [`Min, max element`](#min-max-elements)

&nbsp;&nbsp;&nbsp;[Initializa a stream](#stream-initialization) and then:
* [`Check if all elements are equal`](#Check-if-all-elements-are-equal)
* [`Find maximum integer from the stream`](#Find-maximum-integer-from-the-stream)
* [`Count occurrences of some number in a stream`](#Count-occurrences-of-some-number-in-a-stream)
* [`Get distinct values`](#Get-distinct-values)

</details>

<details>
<summary><b>🎏 Streams</b></summary>

* [`Stream initialization`](#stream-initialization)
* [`Check if all elements are equal`](#check-if-all-elements-are-equal)
* [`Find maximum integer from the stream`](#Find-maximum-integer-from-the-stream)
* [`Count occurrences of some number in a stream`](#Count-occurrences-of-some-number-in-a-stream)
* [`Get distinct values`](#Get-distinct-values)

</details>

<details>
<summary><b>🗺 Maps</b></summary>

* [`Map initialization`](#Map-initialization)
* [`Unmodifiable map initialization`](#Unmodifiable-map-initialization)
* [`Sort map by keys`](#Sort-map-by-keys)
* [`Sort map by values`](#Sort-map-by-values)
* [`Merge two maps`](#Merge-two-maps)

</details>

<details>
<summary><b>👨‍👦 Min Heap, Max Heap, PriorityQueue</b></summary>

* [`Min Heap initialization`](#Min-Heap-initialization)
* [`Max Heap initialization`](#Max-Heap-initialization)

</details>

<details>
<summary><b>📐 Comparators</b></summary>

* [`Comparator.comparing`](#Comparator.comparing)
* [`Comparator reversing`](#Comparator-reversing)
* [`Comparator grouping`](#Comparator-grouping)
* [`Handling null values`](#Handling-null-values)

</details>

<details>
<summary><b>➡ Functional</b></summary>

* [`Common functional interfaces`](#Common-functional-interfaces)
* [`Partial initialization`](#Partial-initialization)

</details>

## 🔢 Arrays

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

### Sort the array

```java
Arrays.sort(array);

Arrays.sort(arr, 1, 5); // sort only elements 1-5

Arrays.sort(arr, Collections.reverseOrder()); 
```

<br>[⬆ back to contents](#Table-of-contents)

### Concatenate two arrays

```java
public static <T> T[] arrayConcat(T[] first, T[] second) {
    var result = Arrays.copyOf(first, first.length + second.length);
    System.arraycopy(second, 0, result, first.length, second.length);
    return result;
}
```
or using streams:
```java
public static <T> T[] concat(T[] first, T[] second) {
    return Stream.concat(
            Stream.of(first),
            Stream.of(second)
    ).toArray(i -> (T[]) Arrays.copyOf(new Object[0], i, first.getClass()));
}
```

<br>[⬆ back to contents](#Table-of-contents)

## 🍱 Sets

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
<br>[⬆ back to contents](#Table-of-contents)

## 🗂 Lists

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

About `Arrays.asList`:
```
Creates a wrapper that implements List<Integer>, which makes the original 
array available as a list. Nothing is copied. Operations are propageted to the
original array. Adding or removing elements from the list are not allowed.
List returned is not usual ArrayList.
```

<br>[⬆ back to contents](#Table-of-contents)

### Unmodifiable list initialization

```java
List<Integer> list = Arrays.asList(1, 2, 3); // can be modified. add, remove is not supported

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

### List sort

Using `Collections`
```java
Collections.sort(list);
Collections.sort(list, Collections.reverseOrder());

Collections.sort(list, (a, b) -> Integer.compare(a.start, b.start))
Collections.sort(list, Comparator.comparingInt(a -> a.start))
```

Using `List.sort(Comparator<? super E> c)`:
```java
list.sort(Comparator.naturalOrder());
list.sort(Comparator.reverseOrder());

list.sort(Collections.reverseOrder());
```

Using `Stream.sorted()`:
```java
List<String> sorted = list.stream()
    .sorted()
    .collect(Collectors.toList());

sorted = list.stream()
    .sorted(Comparator.reverseOrder())
    .collect(Collectors.toList());
```

<br>[⬆ back to contents](#Table-of-contents)

### Binary search

```java
int index = Collections.binarySearch(list, key);
index = Collections.binarySearch(list, key, comparator);
```
<br>[⬆ back to contents](#Table-of-contents)

### Reverse list

```java
Collections.reverse(list);
```
<br>[⬆ back to contents](#Table-of-contents)

### Rotate list

```java
Collections.rotate(list, distance);
```
for example list `1, 2, 3, 4, 5` rotated by distance 2 becomes `4, 5, 1, 2, 3`.
Can be used with negative values.
<br>[⬆ back to contents](#Table-of-contents)

## 📦 Collections

### Min, max elements

```java
Collections.min(collection);
Collections.min(collection, comparator);


Collections.max(collection);
Collections.max(collection, comparator);
```
<br>[⬆ back to contents](#Table-of-contents)

## 🎏 Streams

### Stream initialization

From a `Collection`
```java
Stream<Integer> stream = set.stream();
stream = list.stream();
stream = queue.stream();
```

Using `Stream.of(T…t)`:
```java
Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5, 6, 7, 8, 9);
```

From `array`:
```java
Stream<T> streamOfArray = Arrays.stream(array);
Stream<T> streamOfArray = Stream.of(array);
```
Empty stream:
```java
Stream<String> emptyStream = Stream.empty();
```

Using `Stream.builder()`:
```java
Stream.Builder<String> builder = Stream.builder();
  
Stream<String> stream = builder.add("a")
    .add("b")
    .add("c")
    .build();
```

Using `Stream.iterate()`:
```java
// The iterate() method returns an infinite sequential ordered Stream
// produced by iterative application of a function f to an initial element seed.
Stream.iterate(seedValue, (Integer n) -> n * n)
```

Using `Stream.generate()`:
```java
Stream.generate(Math::random)
```

<br>[⬆ back to contents](#Table-of-contents)

### Check if all elements are equal

```java
return intStream.distinct().count() == 1;
```
<br>[⬆ back to contents](#Table-of-contents)

### Find maximum integer from the stream

```java
return intStream.reduce(Integer.MIN_VALUE, Integer::max);
```
<br>[⬆ back to contents](#Table-of-contents)

### Count occurrences of some number in a stream

```java
return intStream
    .filter(number -> number == value)
    .count();
```
<br>[⬆ back to contents](#Table-of-contents)

### Get distinct values

```java
return intStream.distinct().toArray();
```
<br>[⬆ back to contents](#Table-of-contents)




## 🗺 Maps

### Map initialization

Using `add()`:
```java
Map<String, String> doubleBraceMap  = new HashMap<String, String>() {{
    put("key1", "value1");
    put("key2", "value2");
}};
```
<br>[⬆ back to contents](#Table-of-contents)

### Unmodifiable map initialization

```java
Map<String, String> map = Map.of();

map = Map.of("key", "value");

map = Map.of("key1","value1", "key2", "value2")
    
// ... upto 10 key-value pairs

map = Map.ofEntries(
    new AbstractMap.SimpleEntry<>("key1", "value1"),
    new AbstractMap.SimpleEntry<>("key2", "value2"),
    new AbstractMap.SimpleEntry<>("key3", "value3"),
    new AbstractMap.SimpleEntry<>("key4", "value4")
);
    
map = Collections.singletonMap("key", "value");

map = Collections.emptyMap();
```
<br>[⬆ back to contents](#Table-of-contents)

### Sort map by keys

Using `TreeMap`: 

```java
Map<String, String> sortedMap = new TreeMap<>(map);
```

Using `comparingByKey`:
```java
List<Entry<String, String>> entries = new ArrayList<>(map.entrySet());
entries.sort(Map.Entry.comparingByKey());
// or reversed
entries.sort(Map.Entry.<String, String>comparingByKey().reversed());
```

<br>[⬆ back to contents](#Table-of-contents)

### Sort map by values

Using `comparingByValue`:
```java
List<Entry<String, String>> entries = new ArrayList<>(map.entrySet());
entries.sort(Map.Entry.comparingByValue());
// or reversed
entries.sort(Map.Entry.<String, String>comparingByValue().reversed());
```

<br>[⬆ back to contents](#Table-of-contents)

### Merge two maps

Using `Map.putAll()`:
```java
map1.putAll(map2); // duplicate values will be overridden by values from map2
```

Using `Map.merge()`
```java
map2.forEach((key, value) ->
    map1.merge(key, value, (v1, v2) -> v1 + v2));
// If the specified key is not already associated with a value 
// or is associated with null, the Map.merge() method associates 
// it with the given non-null value.
    
// Otherwise, the Map.merge() method replaces the value with the 
// results of the given remapping function. If the result of the 
// remapping function is null, it removes the key altogether.
```

Using `Stream.concat()`:
```java
Stream<Map.Entry<String, Integer>> combined = Stream.concat(map1.entrySet().stream(), map2.entrySet().stream());
Map<String, Integer> merged = combined.collect(
    Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue));
// in case of duplicate entries this throw an IllegalStateException exception.

// To handle duplicate entries pass a merger function as a third parameter to the collector:
Map<String, Integer> merged = combined.collect(
    Collectors.toMap(Map.Entry::getKey,
           Map.Entry::getValue,
           (v1, v2) -> v1 + v2));
```

<br>[⬆ back to contents](#Table-of-contents)

## 👨‍👦 Min Heap, Max Heap, PriorityQueue

### Min Heap initialization

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

PriorityQueue<Integer> minHeap = new PriorityQueue<>((a, b) -> a - b);

PriorityQueue<Integer> minHeap = new PriorityQueue<>(Comparator.comparingInt(a -> a));

PriorityQueue<Integer> minHeap = new PriorityQueue<>(Comparator.naturalOrder());
```

<br>[⬆ back to contents](#Table-of-contents)

### Max Heap initialization

```java
PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> b - a);

PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());


```

<br>[⬆ back to contents](#Table-of-contents)

## 📐 Comparators

### Comparator.comparing

```java
Comparator.comparing(Employee::getName).reversed();
```

<br>[⬆ back to contents](#Table-of-contents)

### Comparator reversing

```java
Comparator.comparing(Employee::getName).reversed();
```

<br>[⬆ back to contents](#Table-of-contents)

### Comparator grouping

```java
Comparator<Employee> groupByComparator = Comparator.comparing(Employee::getName)
    .thenComparing(Employee::getDob)
    .thenComparing(Employee::getId);
```

<br>[⬆ back to contents](#Table-of-contents)

### Handling null values

```java
Comparator<Employee> comparing =
    comparing(Employee::getName, nullsFirst(naturalOrder()));

Comparator<Employee> comparing =
    comparing(Employee::getName, nullsLast(naturalOrder()));
```

<br>[⬆ back to contents](#Table-of-contents)

## ➡ Functional

### Common functional interfaces

| lamdba                           |        Functional interface        |                                                                                                                                                                                                                               Other interfaces |
|:---------------------------------|:----------------------------------:|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <nobr>`T -> boolean`</nobr>      |    <nobr>`Precdicate<T>`</nobr>    |                                                                                                                                                                                                 `IntPredicate, LongPredicate, DoublePredicate` |
| <nobr>`T -> void`</nobr>         |     <nobr>`Consumer<T>`</nobr>     |                                                                                                                                                                                                     `IntCosumer, LongConsumer, DoubleConsumer` |
| <nobr>`T -> R`</nobr>            |   <nobr>`Function<T, R>`</nobr>    | `IntFunction<R>, IntToDoubleFunctiona, IntToLongFunction, LongFunction<R>, LongToDoubleFunction, LongToIntFunctiction, DoubleFunction<R>, DoubleToIntFunction, DoubleToLongFunction, ToIntFunction<T>, ToDoubleFunction<T>, ToLongFunction<T>` |
| <nobr>`() -> T`</nobr>           |     <nobr>`Supplier<T>`<nobr>      |                                                                                                                                                                                    `BooleanSuppier, IntSupplier, LongSupplier, DoubleSupplier` |
| <nobr>`T -> T`<nobr>             |  <nobr>`UnaryOperator<T>`</nobr>   |                                                                                                                                                                                    `IntUnaryOperator, LongUnaryOperator, DoubleUnaryOperartor` |
| <nobr>`(T, T) -> T`</nobr>       |  <nobr>`BinaryOperator<T>`</nobr>  |                                                                                                                                                                                  `IntBinaryOperator, LongBinaryOperator, DoubleBinaryOperator` |
| <nobr>`(T, U) -> boolean`</nobr> |  <nobr>`BiPredicate<T, U>`</nobr>  |                                                                                                                                                                                                                                                |
| <nobr>`(T, U) -> void`</nobr>    |  <nobr>`BiConsumer<T, U>`</nobr>   |                                                                                                                                                                                  `ObjIntConsumer<T>, ObjLongConsumer<T>, ObjDoubleConsumer<T>` |
| <nobr>`(T, U) -> R`</nobr>       | <nobr>`BiFunction<T, U, R>`</nobr> |                                                                                                                                                                      `ToIntBiFunction<T, U>, ToLongBiFunction<T, U>, ToDoubleBiFunction<T, U>` |

<br>[⬆ back to contents](#Table-of-contents)

### Partial initialization

```java
public interface TriFunction<T, U, V, R> {
  R apply(T t, U u, V v);
}

TriFunction<Integer, Integer, Integer, Integer> add = (x, y, z) -> x + y + z;

Function<Integer, BiFunction<Integer, Integer, Integer>> addPartial = (x) -> (y, z) -> add.apply(x, y, z);

BiFunction<Integer, Integer, Integer> add5 = addPartial.apply(5);

add5.apply(6, 7);
```

<br>[⬆ back to contents](#Table-of-contents)