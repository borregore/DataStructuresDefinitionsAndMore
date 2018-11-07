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
`Arrays.stream(new int[] {1, 2, 3})
    .map(n -> 2 * n + 1)
    .average()
    .ifPresent(System.out::println);`
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
`List<String> result = lines.stream().filter(line -> !"mkyong".equals(line)).collect(Collectors.toList());`
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
`Set<String> results = someDao.findByType(type)
        .stream()
        .map(ClassName::getValue)
        .collect(Collectors.toSet());`
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
`Optional<List> o = id1.entrySet()
                      .stream()
                      .filter( e -> e.getKey() == 1)
                      .map(Map.Entry::getValue)
                      .findFirst();`
### Ordered, sorted or both?
The maps can not be ordered or sorted since they are arranged in the way that they are inserted.
    
## Hashing types
### HashMap: 
Map based collection class that is used for storing Key & value pair. It is not an ordered collection which means it does not return the keys and values in the same order in which they have been inserted. The keys can’t be sorted either. It is unsynchronized and permits nulls(null values and null keys).
#### Class Methods:
* void clear(): It removes all the key and value pairs from the specified Map.
* Object clone(): It returns a copy of all the mappings of a map and used for cloning them into another map.
* boolean containsKey(Object key): It is a boolean function which returns true or false based on whether the specified key is found in the map.
* boolean containsValue(Object Value): Similar to containsKey() method, however it looks for the specified value instead of key.
* Value get(Object key): It returns the value for the specified key.
* boolean isEmpty(): It checks whether the map is empty. If there are no key-value mapping present in the map then this function returns true else false.
* Set keySet(): It returns the Set of the keys fetched from the map.
* value put(Key k, Value v): Inserts key value mapping into the map. Used in the above example.
* int size(): Returns the size of the map – Number of key-value mappings.
* Collection values(): It returns a collection of values of map.
* Value remove(Object key): It removes the key-value pair for the specified key. Used in the above example.
* void putAll(Map m): Copies all the elements of a map to the another specified map.
### HashTable:
Map based collection class that is used for storing Key & value pair. It is not an ordered collection which means it does not return the keys and values in the same order in which they have been inserted. The keys can’t be sorted either. It is synchronized and does not permit nulls.
#### Class methods:
* Object clone(): Creates a shallow copy of this hashtable. All the structure of the hashtable itself is copied, but the keys and values are not cloned. This is a relatively expensive operation.
* boolean contains(Object value): Tests if some key maps into the specified value in this hashtable. This operation is more expensive than the containsKey method.
* boolean isEmpty(): Tests if this hashtable maps no keys to values.
* Enumeration keys(): Returns an enumeration of the keys contained in the hash table.
* Object put(Object key, Object value): Maps the specified key to the specified value in this hashtable.
* void rehash(): Increases the size of the hash table and rehashes all of its keys.
* Object remove(Object key): Removes the key (and its corresponding value) from this hashtable.
* int size(): Returns the number of key-value mappings present in Hashtable.
* String toString(): Returns the string equivalent of a hash table.
* boolean containsKey(Object key): Tests if the specified object is a key in this hashtable.
* boolean containsValue(Object value): Tests if the specified object is a value in this hashtable. Returns true if some value equal to value exists within the hash table. Returns false if the value isn’t found.
* Enumeration elements(): Returns an enumeration of the values contained in the hash table.
* Object get(Object key): Returns the value to which the specified key is mapped, or null if this map contains no mapping for the key. 
### LinkedHashMap:
is a Hash table and linked list implementation of the Map interface, with predictable iteration order. it maintains a doubly-linked list running through all of its entries, which defines the iteration ordering. 
#### Class methods:
* void clear(): It removes all the key and value pairs from the specified Map.
* Object clone(): It returns a copy of all the mappings of a map and used for cloning them into another map.
* boolean containsKey(Object key): It is a boolean function which returns true or false based on whether the specified key is found in the map.
* boolean containsValue(Object Value): Similar to containsKey() method, however it looks for the specified value instead of key.
* Value get(Object key): It returns the value for the specified key.
* boolean isEmpty(): It checks whether the map is empty. If there are no key-value mapping present in the map then this function returns true else false.
* Set keySet(): It returns the Set of the keys fetched from the map.
* value put(Key k, Value v): Inserts key value mapping into the map. Used in the above example.
* int size(): Returns the size of the map – Number of key-value mappings.
* Collection values(): It returns a collection of values of map.
* Value remove(Object key): It removes the key-value pair for the specified key. Used in the above example.
* void putAll(Map m): Copies all the elements of a map to the another specified map.
### ConcurrentHashMap: 
Similar to Hashtable, Synchronized, but faster as multiple locks are used.
### HashSet:
implements the Set interface, backed by a hash table (actually a HashMap instance) which only maintains the keys. It does not guarantee that the order will remain constant over time and permits the null element. It is not synchronized however it can be synchronized explicitly like this: 
`Set s = Collections.synchronizedSet(new HashSet(...));`
### LinkedHashSet: 
implements the Set interface, backed by a hash table (actually a HashMap instance) which only maintains the keys.It maintains the insertion order. It is not synchronized however it can be synchronized explicitly like this: 
`Set s = Collections.synchronizedSet(new LinkedHashSet(...));`

## Difference between == and equals
Main difference between .equals() method and == operator is that one is method and other is operator.
We can use == operators for reference comparison and .equals() method for content comparison. In other words, == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.
## Comparable vs Comparator
A comparable object is capable of comparing itself with another object. The class itself must implements the java.lang.Comparable interface to compare its instances. 
Comparator is external to the element type we are comparing. It’s a separate class. We create multiple separate classes (that implement Comparator) to compare by different members.
If sorting of objects needs to be based on natural order then use Comparable whereas if you sorting needs to be done on attributes of different objects, then use Comparator in Java.
## Generics
A generic type is a generic class, interface or methods that is parameterized over types.
The idea is to allow type (Integer, String, … etc and user defined types) to be a parameter to methods, classes and interfaces.
### Generic class
* To denote that a class is generic we establish the types of data that we want generic in <> then inside of the <> we establish with a capital letter as a  variable that indicates the type of object we want to use inside of our class. Example: 
`public class Test <T>{ 
    T obj; 
    .....
 }`
* We can also use multiple variables to indicate more than one data type that the class can manage. Example: 
`public class Test <T, U>{ 
    T obj1;
    U obj2; 
    .....
}`

### Generic functions
* Functions can be called with different types of arguments based on the type of arguments passed to the generic method, the compiler handles each method.
* To denote that a function is generic first we establish its scope, first in <> we establish the variable of the generic type of data we want to use, then we establish its scope, followed by the return type of data, then the name of the function and inside () we establish the variable to use variable of the type of data with its name. Example: 
`static <T> void genericDisplay (T element) 
    { 
        ..... 
    } ` 




