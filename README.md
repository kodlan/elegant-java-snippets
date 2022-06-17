# elegant-java-snippets
Java code snippets

## Arrays

### Array initialization

```java
int[] array = { 1, 2, 3, 4, 5 };
```

## Lists

### Unmodifiable list initialization

```java
List<Integer> list = Arrays.asList(1, 2, 3);

list = List.of(1, 2, 3);
```

## Sets

## Maps

### Unmodifiable map initialization

```java
Map<String, String> map = Map.of();

map = Map.of("key", "value");

map = Map.of("key1","value1", "key2", "value2")
    
// ... upto 10 key-value pairs

```

## Min Heap, Max Heap, PriorityQueue

