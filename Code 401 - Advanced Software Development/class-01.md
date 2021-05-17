#Class 01

## Big O Notation

## O(1)

##### O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.

```
bool IsFirstElementNull(IList<String> elements)
{
    return elements[0] == null;
}
```

## O(N)

##### O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set. The example below also demonstrates how Big O favours the worst-case performance scenario; a matching string could be found during any iteration of the for loop and the function would return early, but Big O notation will always assume the upper limit where the algorithm will perform the maximum number of iterations.

```
bool ContainsValue(IEnumerable<string> elements, string value)
{
    foreach (var element in elements)
    {
        if (element == value) return true; 
    }     
    return false; 
}
```

## O(N²)

##### O(N²) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. This is common with algorithms that involve nested iterations over the data set. Deeper nested iterations will result in O(N³), O(N⁴) etc.

```
bool ContainsDuplicates(IList<string> elements)
{
    for (var outer = 0; outer < elements.Count; outer++) 
    {
        for (var inner = 0; inner < elements.Count; inner++) 
        { 
            // Don't compare with self 
            if (outer == inner) continue;             
            
            if (elements[outer] == elements[inner]) return true; 
        }
    }    
    return false;
}
```

## O(2^N)

##### O(2^N) denotes an algorithm whose growth doubles with each addition to the input data set. The growth curve of an O(2^N) function is exponential — starting off very shallow, then rising meteorically. An example of an O(2^N) function is the recursive calculation of Fibonacci numbers:

```
int Fibonacci(int number)
{
    if (number <= 1) return number;
       
    return Fibonacci(number - 2) + Fibonacci(number - 1); 
}
```


## Immutable Variables

#### "Change" is unclear

Changing an int: **rebinding**

```
x  = x + 1
```

Changing a list: **mutating**

```
nums.append(7)
```

Can also **rebind** lists:

```
nums = nums + [7]
```
Can't mutate an int because they are **immutable**




### Basic Customizations
`__new__` (self) return a new object (an instance of that class). It is called before `__init__` method.
`__init__` (self) is called when the object is initialized. It is the constructor of a class.
`__del__` (self) for del() function. Called when the object is to be destroyed. Can be used to commit unsaved data or close connections.
`__repr__` (self) for repr() function. It returns a string to print the object. Intended for developers to debug. Must be implemented in any class.
`__str__` (self) for str() function. Return a string to print the object. Intended for users to see a pretty and useful output. If not implemented, `__repr__` will be used as a fallback.
`__bytes__` (self) for bytes() function. Return a byte object which is the byte string representation of the object.
`__format__` (self) for format() function. Evaluate formatted string literals like % for percentage format and ‘b’ for binary.
`__lt__` (self, anotherObj) for < operator.
`__le__` (self, anotherObj) for <= operator.
`__eq__` (self, anotherObj) for == operator.
`__ne__` (self, anotherObj) for != operator.
`__gt__` (self, anotherObj)for > operator.
`__ge__` (self, anotherObj)for >= operator.

## Arithmetic Operators
`__add__` (self, anotherObj) for + operator.
`__sub__` (self, anotherObj) for – operation on object.
`__mul__` (self, anotherObj) for * operation on object.
`__matmul__` (self, anotherObj) for @ operator (numpy matrix multiplication).
`__truediv__` (self, anotherObj) for simple / division operation on object.
`__floordiv__` (self, anotherObj) for // floor division operation on object.

## Type Conversion
`__abs__` (self) make support for abs() function. Return absolute value.
`__int__` (self) support for int() function. Returns the integer value of the object.
`__float__` (self) for float() function support. Returns float equivalent of the object.
`__complex__` (self) for complex() function support. Return complex value representation of the object.
`__round__` (self, nDigits) for round() function. Round off float type to 2 digits and return it.
`__trunc__` (self) for trunc() function of math module. Returns the real value of the object.
`__ceil__` (self) for ceil() function of math module. The ceil function Return ceiling value of the object.
`__floor__` (self) for floor() function of math module. Return floor value of the object.
Emulating Container Types
`__len__` (self) for len() function. Returns the total number in any container.
`__getitem__` (self, key) to support indexing. LIke container[index] calls container.__getitem(key)explicitly.
`__setitem__` (self, key, value) makes item mutable (items can be changed by index), like container[index] = otherElement.
`__delitem__` (self, key) for del() function. Delete the value at the index key.
`__iter__` (self) returns an iterator when required that iterates all values in the container.
Here is a practical use case of `__init__` special method in Python.






> **Here is an example that explains the use of all Special methods mentioned above.**
```
class Account:
    # def __new__(self):
    #     print("__new__ called A new account is Created.")
    def __init__(self, name, balance = 0):
        self.name = name
        self._balance = balance
        print("(__init__) Account Created with {} balance".format(self._balance))
    def getBalance(self):
        return self._balance
    def __repr__(self):
        return "(__repr__) Account({0}, {1})".format(self.name, self._balance)
    def __str__(self):
        return "(__str__) Account Name = {0}, Account Balance = {1}".format(self.name, self._balance)
    def __lt__(self, otherObj):
        try:
            return self._balance<otherObj.getBalance()
        except:
            return "Cannot Be compared."
    def __del__(self):
        self._balance = 0
        print("(__del__) Account Deleted")
    
digvijay_ac = Account("Digvijay Singh", 500)
saket_ac = Account("Digvijay Singh", 700)

print(str(digvijay_ac))
print(repr(digvijay_ac))
print(digvijay_ac<saket_ac)
```
> **Output**
```
(__init__) Account Created with 500 balance
(__init__) Account Created with 700 balance
(__str__) Account Name = Digvijay Singh, Account Balance = 500
(__repr__) Account(Digvijay Singh, 500)
True
(__del__) Account Deleted
(__del__) Account Deleted
```



## References
[Python Dunder (Special, Magic) Methods List with Tutorial](https://holycoders.com/python-dunder-special-methods/)
[Ned Batchelder - Facts and Myths about Python names and values - PyCon 2015](https://www.youtube.com/watch?v=_AEJHKGk9ns)
[A beginner's guide to Big O Notation](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation)