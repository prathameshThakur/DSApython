[![HOME](https://img.shields.io/badge/-HOME-informational?style=plastic)](https://prathameshthakur.github.io/DSApython/)
# <a name='#top'></a>Stack 
This lesson will introduce you to the stack data structure and its implementation in Python which we'll use in the problems throughout this chapter.

We'll cover the following
- [What is a stack?](#what-is-stack)
    - [Stack Operations](#stack-operations)
    - [Push](#push)
    - [Pop](#pop)
    - [Peek](#peek)

- [Determine if Brackets are Balanced](#bracket)
    - [Algorithm](#algo-brack)
    - [Explanation](#exp-brack)

- [Reverse String](#reverse-string)
    - [Algorithm](#algo-string)
    - [Explanation ](#exp-string)


## <a name='what-is-stack'></a> What is a stack?
In this lesson, we are going to consider the stack data structure and its implementation in Python.

In subsequent lessons, we’ll provide specific problems where a stack is particularly useful. We’ll be using the implementation that we develop in this lesson to solve those problems.

First of all, let me describe what a stack is. Based on the name, it should be a relatively familiar concept.

Let’s assume that we have four books with the following riveting titles:

- A
- B
- C
- D

At the moment, these books are strewn out all over the floor and we want to stack them up neatly.

<p align="center">
<img src='images\eg1.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\eg2.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\eg3.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\eg4.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\eg5.PNG' alt='example' style="width:500px;height:250px;"> <br>
</p>

Now we have a nice neat stack of books! If we want to retrieve a book from this stack, we can take the book on top. Taking a book from the bottom is a bit precarious and we don’t want to topple the entire stack. Therefore, we’ll take down the top book on the stack and read it or do whatever we want to do with it.

Let’s say we want to take **Book A**. Right now, it is at the bottom of the stack, so we need to take **Book D**, put it down, then do the same for **Book C** and **Book B**, and then we can access **Book A**.

This is the main idea of a stack. The data structure stack is very similar to a physical stack that you’d most likely be familiar with. The stack data structure allows us to place any programming artifact, variable or object on it, just as our example stack allowed us to put books in it.

## <a name='stack-operations'></a> Stack Operations

### <a name='push'></a> Push
The operation to insert elements in a stack is called push. When we push the book on a stack, we put the book on the previous top element which means that the new book becomes the top element. This is what we mean when we use the push operation, we push elements onto a stack. We insert elements onto a stack and the last element to be pushed is the new top of the stack.

### <a name='pop'></a> Pop
There is another operation that we can perform on the stack, popping. Popping is when we take the top book of the stack and put it down. This implies that when we remove an element from the stack, the stack follows the First-In, Last Out property. This means that the top element, the last to be inserted, is removed when we perform the pop operation.

Push and Pop are two fundamental routines that we’ll need for this data structure.

### <a name='peek'></a> Peek
Another thing that we can do is view the top element of the stack so we can ask the data structure: “What’s the top element?” and it can give that to us using the peek operation. Note that the peek operation does not remove the top element, it merely returns it.

We can also check whether or not the stack is empty, and a few other things too, that will come along the way as we implement it.

Now I’m going to create a stack class, and the constructor of the class is going to initialize a Python list. The Python list has a lot of things that we’re after, and it’s going to make it easier for us to tweak Python’s implementation of the list to be adapted to what we would expect to see in a stack, namely, push/pop.

```python
"""
Stack Data Structure.
"""

class Stack():
    def __init__(self):
        self.items = []
``` 
I’m defining a class variable that I’m calling `items`, and I’m assigning it to an empty list. `self.items` is created when we create a stack object so now let’s create the `push` method:

```python
"""
Stack Data Structure.
"""
class Stack():
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)				
```

`push` is going to be a member of this class, and it’s going to take an `item` as an argument. In our example, that item is the book. We are putting or pushing the name of the book onto the top of the stack.

`append` is a built-in method for a Python list that adds the `item` to the end of the list. This is just what we want to do for our stack in the push method.

The other method we need to implement is `pop`. Since we’re basing this off a list, Python makes this very easy as well. There is an implicit pop method that returns the last element inserted to the list.
```python
"""
Stack Data Structure.
"""
class Stack():
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)				

    def pop(self):
        return self.items.pop()
```

Another thing that we’re going to do is add a few more methods, but before that, I’m going to do a test drive.     

```python
"""
Stack Data Structure.
"""
class Stack():
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)				

    def pop(self):
        return self.items.pop()

    def get_stack(self):
        return self.items

myStack = Stack()
myStack.push("A")
myStack.push("B")
print(myStack.get_stack())
myStack.push("C")
print(myStack.get_stack())
myStack.pop()
print(myStack.get_stack())
```
Output:
```
['A', 'B']
['A', 'B', 'C']
['A', 'B']
```

We make a method called `get_stack()`. This will return the items list, which forms the core of the stack. Then I define a stack object, `myStack`, and push A and B onto the stack. After these operations, I can print `myStack` and the output is `['A', 'B']`. `A` is at the bottom of the stack, and `B` is on the top. Then we push `C` and the output is `['A', 'B', 'C']`, which implies `C` is the top.

We understand the core fundamentals of the stack. A few of the other methods we can include in this are helpful, namely, we could have a method called `is_empty`. It will return whether or not the stack is empty.
<a name='stack.py'></a>
```python
"""
Stack Data Structure.
"""
class Stack():
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)				

    def pop(self):
        return self.items.pop()
    
    def is_empty(self):
        return self.items == []
        
    def get_stack(self):
        return self.items

myStack = Stack()
print(myStack.is_empty()) 
```
Output:
```
True
```

We get `True` here because there’s nothing on the stack at this point. If we push something and call `is_empty()`, we should get `False`. 

```python
"""
Stack Data Structure.
"""
class Stack():
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)				

    def pop(self):
        return self.items.pop()
    
    def is_empty(self):
        return self.items == []
    
    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        
    def get_stack(self):
        return self.items

myStack = Stack()
myStack.push("A")
myStack.push("B")
myStack.push("C")
myStack.push("D")
print(myStack.peek())
```
Output:
```
D
```

Now we have the `peek` operation which tells us the topmost element of the stack.

If `peek` is called on the stack in the above code, it should return `D.peek` checks if the stack is not empty and if it isn’t, it returns the last element of the list, which in this case, is the top element of the stack. We return `self.items[-1]` which is the last item in the list for Python. Hence, at first, we get `D` as the element that Python thinks is on the top of the stack.

Go ahead and create a stack object. You don’t have to limit yourself to letters or strings or anything like that, you could also push numbers. Just play around with this data structure and get a sense of how it works. I’ll see you in the next lesson.

# <a name='bracket'></a>Determine if Brackets are Balanced

This lesson will teach us how to determine whether or not a string has balanced usage of brackets by using a stack.

In this lesson, we’re going to determine whether or not a set of brackets are balanced or not by making use of the stack data structure that we defined in the previous lesson.

Let’s first understand what a balanced set of brackets looks like.

A balanced set of brackets is one where the number and type of opening and closing brackets match and that is also properly nested within the string of brackets.


### Examples of Balanced Brackets 
- { }
- { } { }
- ( ( { [ ] } ) )

### Examples of Unbalanced Brackets 
- ( ( )
- { { { ) } ]

### <a name='algo-brack'></a>Algorithm

Check out the slides below to have a look at the approach we’ll use to solve this problem:


<p align="center">
<img src='images\brc1.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc2.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc3.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc4.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc5.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc6.PNG' alt='example' style="width:500px;height:250px;"> <br>
</p>

As shown above, our algorithm is as follows:

- We iterate through the characters of the string.
- If we get an opening bracket, push it onto the stack.
- If we encounter a closing bracket, pop off an element from the stack and match it with the closing bracket. If it is an opening bracket and of the same type as the closing bracket, we conclude it is a successful match and move on. If it’s not, we will conclude that the set of brackets is not balanced.
- The stack will be empty at the end of iteration for a balanced example of brackets while we’ll be left with some elements in the stack for an unbalanced example.

<p align="center">
<img src='images\brc7.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc8.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc9.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc10.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\brc11.PNG' alt='example' style="width:500px;height:250px;"> <br>
</p>

We’ve covered an example for both the balanced set of brackets and an unbalanced set of brackets, let’s move on to a special case.

### Special Case 
Example: ) )

What if we encounter a closing bracket but don’t have any elements to pop off from the stack? For example, in the case described above, we don’t have an opening parenthesis, but we encounter a closing parenthesis. In this case, we immediately know that the string does not have a balanced usage of brackets. Therefore, we need to watch out for an empty stack in our implementation.

Now that you have got a decent idea of the algorithm, we’ll go over the implementation of it in Python.

Let’s start with the `is_paren_balanced` function:

(You will find the `Stack` class implemented [here](#stack.py))

```python
def is_paren_balanced(paren_string):
    s = Stack()
    is_balanced = True
    index = 0

    while index < len(paren_string) and is_balanced:
        paren = paren_string[index]
        if paren in "([{":
            s.push(paren)
        else:
            if s.is_empty():
                is_balanced = False
                break
            else:
                top = s.pop()
                if not is_match(top, paren):
                    is_balanced = False
                    break
        index += 1

    if s.is_empty() and is_balanced:
        return True
    else:
        return False
```

### <a name='exp-brack'></a>Explanation 
 We declare a stack, `s` and two variables `is_balanced` and `index`, which are set to `True` and `0`, respectively.

The while loop will execute if the `index` is less than the length of paren-string and `is_balanced` is equal to `True`. If any of the conditions evaluate to `False`, our program will exit the while loop. In the while loop, we iterate over each character of the `paren_string` by indexing using the `index` variable and save the indexed element in paren variable.

We check whether `paren` is any type of the opening brackets and if it is, we push it onto the stack. If it’s not any type of the opening brackets, we check if stack `s` is `empty` and set `is_balanced` to `False`. This handles our special case, which we discussed in the previous section.

If the stack is not empty, we pop off the top element and check if the current paren, i.e., a closing bracket matches the type of the top element which is supposed to be an opening bracket. If the types don’t match, then we update `is_balanced` to False.

We increment the index for the next iteration. The while loop keeps executing until the index is equal to or greater than the length of paren_string or `is_balanced` equals `False`.

After we exit the while loop, we check if the stack is empty and is_balanced is `True`, then we return True. Otherwise, we return False.

The code given above is a simple implementation of the algorithm you were introduced to.

Let’s implement the `is_match` function now:

```python
def is_match(`p1`, p2):
    if p1 == "(" and p2 == ")":
        return True
    elif p1 == "{" and p2 == "}":
        return True
    elif p1 == "[" and p2 == "]":
        return True
    else:
        return False
```

### Explanation 
The `is_match` function takes in two characters as `p1` and `p2` and evaluates whether they are a valid pair of brackets. For p1 and `p2` to match, `p1` has to be an opening bracket while `p2` has to be the corresponding closing bracket. If `p1` and `p2` don’t fall in any of the valid conditions, we return `False`.

Easy peasy, right?

The entire implementation of the solution to determine whether a string has a balanced usage of brackets is given below.

```python
from stack import Stack

def is_match(p1, p2):
    if p1 == "(" and p2 == ")":
        return True
    elif p1 == "{" and p2 == "}":
        return True
    elif p1 == "[" and p2 == "]":
        return True
    else:
        return False


def is_paren_balanced(paren_string):
    s = Stack()
    is_balanced = True
    index = 0

    while index < len(paren_string) and is_balanced:
        paren = paren_string[index]
        if paren in "([{":
            s.push(paren)
        else:
            if s.is_empty():
                is_balanced = False
                break
            else:
                top = s.pop()
                if not is_match(top, paren):
                    is_balanced = False
                    break
        index += 1

    if s.is_empty() and is_balanced:
        return True
    else:
        return False

print("String : (((({})))) Balanced or not?")
print(is_paren_balanced("(((({}))))"))

print("String : [][]]] Balanced or not?")
print(is_paren_balanced("[][]]]"))

print("String : [][] Balanced or not?")
print(is_paren_balanced("[][]"))
```

Output:
```
String : (((({})))) Balanced or not?
True
String : [][]]] Balanced or not?
False
String : [][] Balanced or not?
True
```

In the next lesson, we will go over another problem, i.e. reversing a string and solving it using a stack. See you there!

# <a name='reverse-string'></a> Reverse String

In Python, you can reverse a string very easily. For example,
```python
input_str = "hey folks!"
print(input_str[::-1])
```
Output:
```
!sklof yeh
```
However, if you are required to reverse a string using a stack, you can make use of the following algorithm..

### <a name='algo-string'></a> Algorithm 


<p align="center">
<img src='images\str1.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\str2.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\str3.PNG' alt='example' style="width:500px;height:250px;"> <br>
<span>in the similar way we can stack all the words as shown below</span> <br>
<img src='images\str4.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\str5.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\str6.PNG' alt='example' style="width:500px;height:250px;"> <br>
<img src='images\str7.PNG' alt='example' style="width:500px;height:250px;"> <br>
<span>in the similar way we can pop all the words from the stack as shown below</span> <br>
<img src='images\str8.PNG' alt='example' style="width:500px;height:250px;"> <br>

</p>


Isn’t the algorithm pretty straightforward? We push all the characters of the string onto the stack, and due to the First-In, Last-Out property of stack, we get all the characters in reverse order when we pop them off the stack.

Now all that is left for us is to code the algorithm shown above. Let’s do it!

The stack implementation from the first lesson of this chapter has been provided to you in the file `stack.py`. Check out the code below and feel free to play around with it:


### Implementation 

(You will find the `Stack` class implemented [here](#stack.py))

```python
from stack import Stack
def reverse_string(stack, input_str):
  for i in range(len(input_str)):
    stack.push(input_str[i])
  rev_str = ""
  while not stack.is_empty():
    rev_str += stack.pop()

  return rev_str

stack = Stack()
input_str = "!gninrael yppaH"
print(reverse_string(stack, input_str))
```
Output:
```
Happy learning!
```

### <a name='exp-string'></a> Explanation

Let’s discuss the `reverse_string` function in the code above. The for loop iterates over `input_str` and pushes each character on to `stack`. Then we initialize `rev_str` as an empty string. We pop off all the elements from the stack and append them to `rev_str` one by one until the stack becomes empty and terminates the while loop. We return then `rev_str`.

Easy, right? You can test your understanding and skills in the exercise in the next lesson.



[![TOP](https://img.shields.io/badge/-Go%20to%20top-grey?style=plastic)](#top)