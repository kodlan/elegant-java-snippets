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
* [`All intermediate and terminal operations`](#All-intermediate-and-terminal-operations)
* [`IntStream methods`](#int-stream)
* [`LongStream methods`](#long-stream)
* [`DoubleStream methods`](#double-stream)
* [`Collectors`](#collectors-methods)
* [`Check if all elements are equal`](#check-if-all-elements-are-equal)
* [`Find maximum integer from the stream`](#Find-maximum-integer-from-the-stream)
* [`Count occurrences of some number in a stream`](#Count-occurrences-of-some-number-in-a-stream)
* [`Get distinct values`](#Get-distinct-values)
* [`All pairs of numbers from two lists`](#All-pairs-of-numbers-from-two-lists)


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
* [`Handling exceptions when interface doesn't throw exception`](#functional-handle-exception)
* [`Constructor references`](#Constructor-references)

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

### All intermediate and terminal operations

| Operation         | Type                              | Return type    | Fn interface               | Fn descriptor       |
|:------------------|:----------------------------------|:---------------|:---------------------------|:--------------------|
| `filter`          | Intermediate                      | `Stream<T>`    | `Predicate<T>`             | `T -> boolean`      |
| `distinct`        | Intermediate (stateful-unbounded) | `Stream<T>`    |                            |                     |
| `takeWhile`       | Intermediate                      | `Stream<T>`    | `Predicate<T>`             | `T -> boolean`      |
| `dropWhile`       | Intermediate                      | `Stream<T>`    | `Predicate<T>`             | `T -> boolean`      |
| `skip`            | Intermediate (stateful-bounded)   | `Stream<T>`    | `long`                     |                     |
| `limit`           | Intermediate (stateful-bounded)   | `Stream<T>`    | `long`                     |                     |
| `map`             | Intermediate                      | `Stream<R>`    | `Function<T, R>`           | `T -> R`            |
| `mapToDouble`     | Intermediate                      | `DoubleStream` | `ToDoubleFunction<T>`      | `T -> DoubleStream` |
| `mapToInt`        | Intermediate                      | `IntStream`    | `ToIntFunction<T>`         | `T -> IntStream`    |
| `mapToLong`       | Intermediate                      | `LongStream`   | `ToLongFunction<T>`        | `T -> LongStream`   |
| `flatMap`         | Intermediate                      | `Stream<R>`    | `Function<T, Stream<R>>`   | `T -> Stream<R>`    |
| `flatMapToDouble` | Intermediate                      | `DoubleStream` | `Function<T, DoubleStream>` | `T -> DoubleStream` |
| `flatMapToInt`    | Intermediate                      | `IntStream`    | `Function<T, IntStream>`   | `T -> IntStream`    |
| `flatMapToLong`   | Intermediate                      | `LongStream`   | `Function<T, LongStream>`  | `T -> LongStream`   |
| `sorted`          | Intermediate (stateful-unbounded) | `Stream<T>`    | `Comparator<T>`            | `(T, T) -> int`     |
| `anyMatch`        | Terminal                          | `boolean`      | `Predicate<T>`             | `T -> boolean`      |
| `noneMatch`       | Terminal                          | `boolean`      | `Predicate<T>`             | `T -> boolean`      |
| `allMatch`        | Terminal                          | `boolean`      | `Predicate<T>`             | `T -> boolean`      |
| `findAny`         | Terminal                          | `Optional<T>`  |                            |                     |
| `findFirst`       | Terminal                          | `Optional<T>`  |                            |                     |
| `forEach`         | Terminal                          | `void`         | `Consumer<T>`              | `T -> void`         |
| `collect`         | Terminal                          | `R`            | `Collector<T, A, R>`       |                     |
| `reduce`          | Terminal (stateful-bounded)       | `Optional<T>`  | `BinaryOperaror<T>`        | `(T, T) -> T`       |
| `count`           | Terminal                          | `long`         |                            |                     |
| `max`             | Terminal                          | `Optional<T>`  | `Comparator<T>`            |                     |
| `min`             | Terminal                          | `Optional<T>`  | `Comparator<T>`            |                     |

`bounded` - the internal state is of bounded size no matter how many elements are in the stream being processed

`unbounded` - for example, sorting requires all the elements to be buffered before single item
can be added to the output stream.

`stateful` - requires processing of all the elements in the stream (the largest number for example)

<br>[⬆ back to contents](#Table-of-contents)

<a name="int-stream"></a>
### IntStream methods (not all of them)

| Method           | Signature                                                    |
|:-----------------|:-------------------------------------------------------------|
| `allMatch`       | `boolean allMatch(IntPredicate predicate)`                   |
| `anyMatch`       | `boolean anyMatch(IntPredicate predicate)`                   |
| `asDoubleStream` | `DoubleStream asDoubleStream()`                              |
| `asLongStream`   | `LongStream asLongStream()`                                  |
| `average`        | `OptionalDouble average()`                                   |
| `boxed`          | `Stream<Integer> boxed()`                                    |
| `count`          | `long count()`                                               |
| `distinct`       | `IntStream distinct()`                                       |
| `filter`         | `IntStream filter(IntPredicate predicate)`                   |
| `findAny`        | `OptionalInt findAny()`                                      |
| `findFirst`      | `OptionalInt findFirst()`                                    |
| `flatMap`        | `IntStream flatMap(IntFunction<? extends IntStream> mapper)` |
| `forEach`        | `IntStream forEach(IntConsumer action)`                      |
| `limit`          | `IntStream limit(long maxSize)`                              |
| `map`            | `IntStream map(IntUnaryOperator mapper)`                     |
| `mapToDouble`    | `DoubleStream mapToDouble(IntToDoubleFunction mapper)`       |
| `mapToLong`      | `LongStream mapToLong(IntToLongFunction mapper)`             |
| `mapToObj`       | `<U> Stream<U> mapToObj(IntFunction<? extends U> mapper)`    |
| `max`            | `OptionalInt max()`                                          |
| `min`            | `OptionalInt min()`                                          |
| `noneMatch`      | `boolean noneMatch(IntPredicate predicate)`                  | 
| `parallel`       | `IntStream parallel()`                                       |
| `reduce`         | `OptionalInt reduce(IntBinaryOperator op)`                   |
| `reduce`         | `OptionalInt reduce(int identity, IntBinaryOperator op)`     |
| `sequential`     | `IntStream sequential()`                                     |
| `skip`           | `IntStream skip(long n)`                                     |
| `sorted`         | `IntStream sorted()`                                         |
| `sum`            | `int sum()`                                                  |
| `toArray`        | `int[] toArray()`                                            |

Static initialization method:

| Method        | Signature                                                            |
|:--------------|:---------------------------------------------------------------------|
| `concat`      | `static IntStream concat(IntStream a, IntStream b)`                  |
| `empty()`     | `static IntStream empty()`                                           |
| `generate`    | `static IntStream generate(IntSupplier s)`                           |
| `iterate`     | `static IntStream iterate(int seed, IntUnaryOperator f)`             |
| `of`          | `static IntStream of(int... values)`                                 |
| `of`          | `static IntStream of(int t)`                                         |
| `range`       | `static IntStream range(int startInclusive, int endExclusive)`       |
| `rangeClosed` | `static IntStream rangeClosed(int startInclusive, int endInclusive)` |

 
<br>[⬆ back to contents](#Table-of-contents)

<a name="long-stream"></a>
### LongStream methods (not all of them)

| Method           | Signature                                                       |
|:-----------------|:----------------------------------------------------------------|
| `allMatch`       | `boolean allMatch(LongPredicate predicate)`                     |
| `anyMatch`       | `boolean anyMatch(LongPredicate predicate)`                     |
| `asDoubleStream` | `DoubleStream asDoubleStream()`                                 |
| `average`        | `OptionalDouble average()`                                      |
| `boxed`          | `Stream<Long> boxed()`                                          |
| `count`          | `long count()`                                                  |
| `distinct`       | `LongStream distinct()`                                         |
| `filter`         | `LongStream filter(LongPredicate predicate)`                    |
| `findAny`        | `OptionalLong findAny()`                                        |
| `findFirst`      | `OptionalLong findFirst()`                                      |
| `flatMap`        | `LongStream flatMap(LongFunction<? extends LongStream> mapper)` |
| `forEach`        | `LongStream forEach(LongConsumer action)`                       |
| `limit`          | `LongStream limit(long maxSize)`                                |
| `map`            | `LongStream map(LongUnaryOperator mapper)`                      |
| `mapToDouble`    | `DoubleStream mapToDouble(LongToDoubleFunction mapper)`         |
| `mapToInt`       | `IntStream mapToLong(LongToIntFunction mapper)`                 |
| `mapToObj`       | `<U> Stream<U> mapToObj(IntFunction<? extends U> mapper)`       |
| `max`            | `OptionalLong max()`                                            |
| `min`            | `OptionalLong min()`                                            |
| `noneMatch`      | `boolean noneMatch(LongPredicate predicate)`                    | 
| `parallel`       | `LongStream parallel()`                                         |
| `reduce`         | `OptionalLong reduce(LongBinaryOperator op)`                    |
| `reduce`         | `OptionalLong reduce(long identity, LongBinaryOperator op)`     |
| `sequential`     | `LongStream sequential()`                                       |
| `skip`           | `LongStream skip(long n)`                                       |
| `sorted`         | `LongStream sorted()`                                           |
| `sum`            | `long sum()`                                                    |
| `toArray`        | `long[] toArray()`                                              |

Static initialization method:

| Method        | Signature                                                               |
|:--------------|:------------------------------------------------------------------------|
| `concat`      | `static LongStream concat(LongStream a, LongStream b)`                  |
| `empty()`     | `static LongStream empty()`                                             |
| `generate`    | `static LongStream generate(LongSupplier s)`                            |
| `iterate`     | `static LongStream iterate(int seed, LongUnaryOperator f)`              |
| `of`          | `static LongStream of(long... values)`                                  |
| `of`          | `static LongStream of(long t)`                                          |
| `range`       | `static LongStream range(long startInclusive, long endExclusive)`       |
| `rangeClosed` | `static LongStream rangeClosed(long startInclusive, long endInclusive)` |

<br>[⬆ back to contents](#Table-of-contents)

<a name="double-stream"></a>
### DoubleStream methods (not all of them)

| Method       | Signature                                                             |
|:-------------|:----------------------------------------------------------------------|
| `allMatch`   | `boolean allMatch(DoublePredicate predicate)`                         |
| `anyMatch`   | `boolean anyMatch(DoublePredicate predicate)`                         |
| `average`    | `OptionalDouble average()`                                            |
| `boxed`      | `Stream<Double> boxed()`                                              |
| `count`      | `Double count()`                                                      |
| `distinct`   | `DoubleStream distinct()`                                             |
| `filter`     | `DoubleStream filter(DoublePredicate predicate)`                      |
| `findAny`    | `OptionalDouble findAny()`                                            |
| `findFirst`  | `OptionalDouble findFirst()`                                          |
| `flatMap`    | `DoubleStream flatMap(DoubleFunction<? extends DoubleStream> mapper)` |
| `forEach`    | `DoubleStream forEach(DoubleConsumer action)`                         |
| `limit`      | `DoubleStream limit(double maxSize)`                                  |
| `map`        | `DoubleStream map(DoubleUnaryOperator mapper)`                        |
| `mapToLong`  | `DoubleStream mapToLong(DoubleToLongFunction mapper)`                 |
| `mapToInt`   | `IntStream mapToDouble(DoubleToIntFunction mapper)`                   |
| `mapToObj`   | `<U> Stream<U> mapToObj(IntFunction<? extends U> mapper)`             |
| `max`        | `OptionalDouble max()`                                                |
| `min`        | `OptionalDouble min()`                                                |
| `noneMatch`  | `boolean noneMatch(DoublePredicate predicate)`                        | 
| `parallel`   | `DoubleStream parallel()`                                             |
| `reduce`     | `OptionalDouble reduce(DoubleBinaryOperator op)`                      |
| `reduce`     | `OptionalDouble reduce(double identity, DoubleBinaryOperator op)`     |
| `sequential` | `DoubleStream sequential()`                                           |
| `skip`       | `DoubleStream skip(long n)`                                           |
| `sorted`     | `DoubleStream sorted()`                                               |
| `sum`        | `double sum()`                                                        |
| `toArray`    | `double[] toArray()`                                                  |

Static initialization method:

| Method        | Signature                                                                 |
|:--------------|:--------------------------------------------------------------------------|
| `concat`      | `static DoubleStream concat(DoubleStream a, DoubleStream b)`              |
| `empty()`     | `static DoubleStream empty()`                                             |
| `generate`    | `static DoubleStream generate(DoubleSupplier s)`                          |
| `iterate`     | `static DoubleStream iterate(int seed, DoubleUnaryOperator f)`            |
| `of`          | `static DoubleStream of(long... values)`                                  |
| `of`          | `static DoubleStream of(long t)`                                          |
| `range`       | `static DoubleStream range(long startInclusive, long endExclusive)`       |
| `rangeClosed` | `static DoubleStream rangeClosed(long startInclusive, long endInclusive)` |

<br>[⬆ back to contents](#Table-of-contents)


### Collectors methods
`Collector<T,A,R>`:

T - the type of input elements to the reduction operation

A - the mutable accumulation type of the reduction operation (often hidden as an implementation detail)

R - the result type of the reduction operation

| Return type                              | Method (concurent methods skipped, all methods are static)                                                                                                |
|:-----------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Collector<T,?,Double>`                  | `averagingDouble(ToDoubleFunction<? super T> mapper)`                                                                                                     |
| `Collector<T,?,Double>`                  | `averagingInt(ToIntFunction<? super T> mapper)`                                                                                                           |
| `Collector<T,?,Double>`                  | `averagingLong(ToLongFunction<? super T> mapper)`                                                                                                         |
| `Collector<T,A,RR>`                      | `collectingAndThen(Collector<T,A,R> downstream, Function<R,RR> finisher)`                                                                                 |
| `Collector<T,?,Long>`                    | `counting()`                                                                                                                                              |
| `Collector<T,?,Map<K,List<T>>>`          | `groupingBy(Function<? super T,? extends K> classifier)`                                                                                                  |
| `Collector<T,?,Map<K,D>>`                | `groupingBy(Function<? super T,? extends K> classifier, Collector<? super T,A,D> downstream)`                                                             |
| `Collector<T,?,M extends Map<K,D>>`      | `groupingBy(Function<? super T,? extends K> classifier, Supplier<M> mapFactory, Collector<? super T,A,D> downstream)`                                     |
| `Collector<CharSequence,?,String>`       | `joining()`                                                                                                                                               |
| `Collector<CharSequence,?,String>`       | `joining(CharSequence delimiter)`                                                                                                                         |
| `Collector<CharSequence,?,String>`       | `joining(CharSequence delimiter, CharSequence prefix, CharSequence suffix)`                                                                               |
| `Collector<T,?,R>`                       | `mapping(Function<? super T,? extends U> mapper, Collector<? super U,A,R> downstream)`                                                                    |
| `Collector<T,?,Optional<T>>`             | `maxBy(Comparator<? super T> comparator)`                                                                                                                 |
| `Collector<T,?,Optional<T>>`             | `minBy(Comparator<? super T> comparator)`                                                                                                                 |
| `Collector<T,?,Map<Boolean,List<T>>>`    | `partitioningBy(Predicate<? super T> predicate)`                                                                                                          |
| `Collector<T,?,Map<Boolean,D>>`          | `partitioningBy(Predicate<? super T> predicate, Collector<? super T,A,D> downstream)`                                                                     |
| `Collector<T,?,Optional<T>>`             | `reducing(BinaryOperator<T> op)`                                                                                                                          |
| `Collector<T,?,T>`                       | `reducing(T identity, BinaryOperator<T> op)`                                                                                                              |
| `Collector<T,?,U>`                       | `reducing(U identity, Function<? super T,? extends U> mapper, BinaryOperator<U> op)`                                                                      |
| `Collector<T,?,DoubleSummaryStatistics>` | `summarizingDouble(ToDoubleFunction<? super T> mapper)`                                                                                                   |
| `Collector<T,?,IntSummaryStatistics>`    | `summarizingInt(ToIntFunction<? super T> mapper)`                                                                                                         |
| `Collector<T,?,LongSummaryStatistics>`   | `summarizingLong(ToLongFunction<? super T> mapper)`                                                                                                       |
| `Collector<T,?,Double>`                  | `summingDouble(ToDoubleFunction<? super T> mapper)`                                                                                                       |
| `Collector<T,?,Integer>`                 | `summingInt(ToIntFunction<? super T> mapper)`                                                                                                             |
| `Collector<T,?,Long>`                    | `summingLong(ToLongFunction<? super T> mapper)`                                                                                                           |
| `Collector<T,?,C extends Collection<T>>` | `toCollection(Supplier<C> collectionFactory)`                                                                                                             |
| `Collector<T,?,List<T>>`                 | `toList()`                                                                                                                                                |
| `Collector<T,?,Map<K,U>>`                | `toMap(Function<? super T,? extends K> keyMapper, Function<? super T,? extends U> valueMapper)`                                                           |
| `Collector<T,?,Map<K,U>>`                | `toMap(Function<? super T,? extends K> keyMapper, Function<? super T,? extends U> valueMapper, BinaryOperator<U> mergeFunction)`                          |
| `Collector<T,?,M extends Map<K,U>>`      | `toMap(Function<? super T,? extends K> keyMapper, Function<? super T,? extends U> valueMapper, BinaryOperator<U> mergeFunction, Supplier<M> mapSupplier)` |
| `Collector<T,?,Set<T>>`                  | `toSet()`                                                                                                                                                 |

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

### All pairs of numbers from two lists

```java
List<Integer> numbers1 = Arrays.asList(1, 2, 3);
List<Integer> numbers2 = Arrays.asList(4, 5, 6);

List<int[]> pairs = numbers1.stream()
    .flatMap(i -> numbers2.stream()
        .map(j -> new int[] {i, j}))
    .collect(toList());
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
Comparator.comparing(Employee::getName, comparator).reversed();

// or 
Comparator.comparingInt(Employee::getIntValue);
Comparator.comparingDouble(Employee::getDoubleValue);
Comparator.comparingLong(Employee::getLongValue);
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

// also
Comparator.thenComparingInt(Employee::getIntValue);
Comparator.thenComparingDouble(Employee::getDoubleValue);
Comparator.thenComparingLong(Employee::getLongValue);
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

<a name="functional-handle-exception"></a>
### Handling exceptions when interface doesn't throw exception
For example in case of Runnable:

```java
@FunctionalInterface
public interface Runnable {
  public abstract void run();
}
```

Create a Thread using lambda that throws exception:
```java
new Thread(() -> {
      try {
        methodThatThrowsException();
      } catch (Exception e) {
        // do something
      }
    });
```

To fix the try/catch in lambda, add ThrowingRunnable interface:
```java
@FunctionalInterface
public interface ThrowingRunnable<E extends Exception> {

  void run() throws E;

  static <E extends Exception> Runnable handleThrowingRunnable(
      ThrowingRunnable<E> throwingRunnable, Consumer<Exception> handler) {

    return () -> {
      try {
        throwingRunnable.run();
      } catch (Exception ex) {
        handler.accept(ex);
      }
    };
  }
}
```

And then:

```java
new Thread(
    ThrowingRunnable.handleThrowingRunnable(
        this::methodThatThrowsException,
        exception -> logger.info("Something happened", exception))));
```

<br>[⬆ back to contents](#Table-of-contents)

### Constructor references

```java
Supplier<Apple> appleSupplier = Apple::new;
Apple apple = appleSupplier.get();

// or if constructor has arguments:

BiFunction<Color, Integer, Apple> supplier = Apple::new;
Apple apple = supplier.apply(GREEN, 110);
```

<br>[⬆ back to contents](#Table-of-contents)