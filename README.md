# DataStructuresDefinitionsAndMore

# Data Structures
## Arrays
### Definition:
It’s a data structure that stores a fixed-sized sequential collection of elements of the same type that have a contiguous memory location.
### Big O:
* Access: O(1)
* Search: O(n)
* Insertion: O(n)
* Deletion: O(n)
### How to manage growth: 
The array does not manage growth since it is a fixed-sized collection of elements.
Thread safe: The array alone is not thread safe, but when you implement a synchronization method from the collection class it will make it thread safe, this way 2 or more methods won’t be able to modify the array at the same time since the synchronized method will force the thread to wait until the array method is finished.
### Interface base methods: 
* binarySearch(Object[] a, Object key)
* copyOf(long[] original,int newLength)
* copyOfRange(short[] original, int from, int to)
* equals(long[] a, long[] a2)
* fill(int[] a, int val)
* sort()
* toString()
### Streams:
Arrays.stream(new int[] {1, 2, 3})
    .map(n -> 2 * n + 1)
    .average()
    .ifPresent(System.out::println);
### Ordered, sorted or both?
The array can be sorted thanks to its base method in the interface called sort() and can be ordered with the help of the Collections class.
## ArrayList
### Definition
It’s a dynamic array that grows as needed which implements the List interface.
### Big O: 
* Access: O(1)
* Search: O(n)
* Insertion: O(1)
* Deletion: O(n)
### How to manage growth: 
A new array is created and the contents of the old array are copied over the new one. The old array becomes eligible for garbage collection, like any object that no longer has anything referencing it. When (or even if) that happens is up to the JVM.
Thread safe: The ArrayList is not thread safe since it has to iterate through the hole list and can be paused at the middle of a method  to let another thread make a modification, this alters the results. The arrayList can be used with a synchronized list that allows it to be thread safe.
### Interface base methods: 
* Add(int index, Object element)
* add(Object o)
* addAll(Collection c)
* addAll(int index, Collection c)
* clear()
* clone()
* contains(Object o)
* ensureCapacity(int minCapacity)
* get(int index)
* indexOf(Object o)
* lastIndex(Object o)
* remove(int index)
* removeRange(int fromIndex, int toIndex)
* set(int index, Object o)
* size()
trimtoSize()
### Streams:
List<String> result = lines.stream().filter(line -> !"mkyong".equals(line)).collect(Collectors.toList());
### Ordered, sorted or both? 
The ArrayList can be sorted or ordered thanks to the collection class.

## Sets
### Definition
It’s a data structure that represents a collection of objects where each object in the set is unique.
### Big O: 
* Access: O(n)
* Search: O(n)
* Insertion: O(n)
* Deletion: O(n)
### Differences between sets and lists:
A set only contains unique elements and the list does not.
Elements in a set has no guaranteed internal order, meanwhile the elements in a list has an internal order which can be iterated in that order.
### How to manage growth: 
A HashSet is backed by a HashMap. The size doubles each time an increase is needed, it actually adds a new entry into the table.
### Thread safe: 
The HashSet is not thread safe. In Java 8 there is a new method added into a concurrent HashMap which is newKeySet() which allows us to create a concurrent HashSet backed by a concurrentHashMap which allows us to have a thread safe set. It can also be thread safe by implementing the synchronized method from the Collection class. 
### Interface base methods:
* add(Object o)
* clear()
* contains(Object  o)
* isEmpty()
* remove(Object o)
* size()
### Streams:
Set<String> results = someDao.findByType(type)
        .stream()
        .map(ClassName::getValue)
        .collect(Collectors.toSet());
### Ordered, sorted or both?
The sets can not be ordered or sorted since they are arranged in the way they are inserted.

## Maps
### Definition
It’s a collection that maps unique keys to values. A key is an object that you use to retrieve a value at a later date.
### Big O:
* Access: O(n)
* Search: O(n)
* Insertion: O(n)
* Deletion: O(n)
### How to manage growth: 
When a hashMap resizes, it will double in size and create a new instance and populate it. When new HashMap is being populated, the linkedList associated with each bucket of source hashMap is iterated and nodes are copied to the destination bucket. However, note that these new nodes are prepended to the head of the destination linkedList. So resizing has an side effect of reversing the order of the items in the list. Default load factor for hashMap is 0.75
### Thread safe: 
Maps are not thread safe but there are several classes that can help with that. They are HashTable (which is inefficient), SynchronizedMap which is far superior in efficiency than HashMap; that allow us to have a thread safe map.
### Interface base methods:
* clear()
* containsKey(Object k)
* containsValue(Object v)
* entrySet()
* equals(Object o)
* get(Object k)
* hashCode()
* isEmpty()
* keySet()
* put(Object k, Object v)
### Streams:
Optional<List> o = id1.entrySet()
                      .stream()
                      .filter( e -> e.getKey() == 1)
                      .map(Map.Entry::getValue)
                      .findFirst();
### Ordered, sorted or both?
The maps can not be ordered or sorted since they are arranged in the way that they are inserted.
