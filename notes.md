# Top
# 01/07/20  
## Syllabus Week (day 1)  
* About the course  
* Math Review  
*Lvalues* are values that are object names that are modifiable although they can be non-modifiable (in cases where the object is const)  
*Rvalues* are the literal values (10, a), or temporary values that can be altered (x + y)  
One can have references to both *lvalues and rvalues*  
An *Lvalue reference* is `string str = "hell"; string& rstr = str;`  
An *Rvalues refernece* is `string && name = "test";`, rvalue references have &&  
Lvalues are used often, rvalues are taught later as their use isn't as obvious    
Good uses of lvalues is to:  
* Rename and alias complex variable names  
* Use in range loops  
	* Illegal: `for (auto x : arr)`  
	* Legal: `for (auto& x : arr)`
* Avoiding a copy  

**Big O Notation**     
![Big O Complexity Chart](./BigOComplexityChart.png)
*O(1)*  
* Is notation where the run time will always be the same no matter the variable size of input    
* Ex. Function to check if first item in array is null  
*O(N)*  
* Is a representation of a linear growth of a function and it's runtime, always assumes the worst case so even if it can terminate early that won't happen  
* Ex. Function that compares two strings and returns bool if matching strings are found  
*O(N^2)*  
* Is where multiple loops are used to search through something where the power of two is using two nested loops, power of 3 is three nested loops, etc.   
* Ex. Looping through 2D arrays or searching for letters in an array of strings  
*O(2^N)*  
* Is a recursive functions growing exponentially each time the program is run  
* Ex. Fibonacci sequence that calls itself or any other recursive function  
*O(LogN)*  
* Is best used in a example of a binary search, where the search field is split in half and continually split to find a result; this method is initially bulky but then is less intense as the program continues  
* Ex. Binary search through a sorted array for a certain number

Big emphasis in this class on finding how prgrams grow in intensity as the input size grows to infinity    
General search algorithm is O(N) complex (on a graph gets more intense by linear line)  
Divide and Search (split array in half and look in each section) is O(N/2) complex (on graph looks like logN graph)  
For finding Kth largest number in group of N numbers?  
Decent method:  
* Sort K first   
* Insert elements (k + 1) to N discarding smallest element each time  
* Then pick the Kth item  
(This is a slow way to do this)  
Log is always base 2, unless specified   

# 01/09/20  
## Recursion  
To read thru and test logic of recursive functions step through the functions with the starting value and a place holder for the next call of its own function with the next case in parenthesis to keep track, solve until it would end then go back through each function and start solving  
Ex. f(x) = 2 f(x - 1) + x^2  
*Bookkeeping*  
1. f(3) = 2 * f(2) + 3 * 3    
2. f(2) = 2 * f(1) + 2 * 2  
3. f(1) = 2 * f(0) + 1 * 1  
4. f(0) = 0    
*Backtracking*  
3. f(1) = 2 * 0 + 1 * 1 = 1  
2. f(2) = 2 * 1 + 2 * 2 = 6  
1. f(3) = 2 * 6 + 3 * 3 = 21  
**Two main rules of recursive functions**:
1. Always need an escape value and to create value checking so if a negative is passed to the function above it doesn't continue infinitely   
2. Always be incrementing towards the base case to escape and terminate  
*Further important rules*:  
3. Assume all recursive calls work  
4. Never duplicate work by calling recursive functions twice  

## C++ Review  
**Classes**  
Constructor set up like `explicit IntCell(int initialValue = 0):storedValue{initialValue}{}` to only call IntCell only explicitly with curly brackets (in accord with c++ 11, not ()) with 0 used if no value is passed  
To prevent `obj = 37;` being converted automatically to IntCell type the one parameter constructor needs explicitly so it is not seen as a conversion constructor  
Interface is the header file, Implementation is the file that uses it (usually main, when `#include "header.h"`)  
Use `#ifndef HEADER_H #define HEADER_H` and `#endif` to compile header file and ensure it is not implemented more than once  
**Uses curly braces in C++ 11 when passing parameters to objects**  
*Always use vector and string libraries unless specifically building a program for speed*  
* Vector library has size() built in and can use = to assign values  
* String can be compared, assigned with =, and has length() function builtin   
Vector initialization is by `vector<int> vec1 = {10, 20, 30};`  
If one does `vector<int> vec2(10);` will create vector of size 10, but `vector<int> vec3{12}` will initialize 12 as a value of vec3  
**Curly braces in vectors is to initialize values**  
Range-based loops are by:  
```  
int sum = 0;  
for (int x : squares) {
		sum += x;
}  
```  
C++ 11 also has *auto* datatype, meaning the compiler will look and try to automatically assign datatype to variable being used  
Lvalues can only be copied, ex. y = 5 and x = y means x will equal 5 after a copy is made  
Rvalues can be moved, ex. string str = "hello" and string && str2 = "hello" the first is an lvalue but the second is an rvalue that can be moved and is more efficient  
To change an Lvalue into an Rvalue use std::move(str)  
```  
string x = "hello";  
string y = x;  
```  
The above will make to instances of "hello" both in y and x  
To avoid this do the below  
```  
string x = "hello";  
string & y = x;  
```  
This above one will have x contain the string and y becomes a reference variable directly to the same value contained in x  

# 01/13/20
1. Prints all files starting with po and followed by anything 
2. Prints the contents of any files that are followed by 1 through 6 and overwrites all the output into file temp  
3. x = 2  
4. i = 36, j = 4, k = 2
5. Code below:    
```
class MyInt {
		public:    
			MyInt(int);
			int const get();  
			bool set();
		private:      
			int data;
}  
```  
6. Code below:  
 
```  
MyInt::MyInt (int value) {
		data = value;  
}  
```  
7. Code below:  
```  
MyInt::int const get() {
		return data;
}  
```  
8. const int \*X means that x will always be the same memory location being pointed to and int \*const int means that the value X points to will always be the same  
9. So that a deep copy is made and that the pointers being copied point to  a copied array and not a pseudo clone of the first array  
10. delete [] ptr;  

# 01/21/20
Big O Evaluation of programs  
n is size of input  
Each primitive operation is one unit of time  
Find f(n) = number of atomic activities  
Complexity of algorithm = complexity of f(n)  
In for loop with 3 primitive functions == 3n  
* Initialize  
* n increment   
* Comparison of j and n
Each increment is Theta(n)    
In a for loop:   
```
for (j = 0; j < n; ++j) {
		// 2 atomic  
		for (k = 0; k < n; ++k) {
				// 3 atomics
		}
}  
```  
Complexity: Theta((2 + 3n)n) = Theta(n²)   
[To review complexity](./ch2_algorithmAnalysis.pdf)  

# 01/23/20
O(1) < O(log^log(n))< O(log(n)) < O((log(n)^c) (c > 1) < O(n^c) (0 < c < 1) < O(n) < O(n * log(n)) < log(n)! < O(n²) < O(n^c) (c > 2) < O(2^n) < O(n!)  
Which grows fastest? 2^n, n!, N^log(n)  
O(n!) > O(2^n)  
Example:   
```  
long f (int n) {
		if (n <= 1)  
				return 1;  
		else  
				return 1 + f(n-1);
}  
```  
t(1) = 1    
t(n) = 2 + t(n-1)  
We know t(n-2) = 2 + t(n-3) and t(n-3) = 2 + t(n-4)  
Substitute  
t(n) == 2 + (2 + t(n-3)) == 2 + (2 + (2 + t(n-4)))  
each term you add a +2, have to find base case at k  
2k + t(n-k)  
Final **O(n)**  
  
Example:  
f(1) = 5  
f(n) = 5 + 5 * f(n-1) + 2 * f(n-1)  
t(1) = 1  
t(n) = 5 + 2 * t(n-1)  
5 + 2 (5 + 2² (5 + 2³ (5 + 2⁴ t(n-4))))  
t(n) = 5 2⁰ + 5 2¹ + 5 2² + 5 2³ + ... + 2^k  
5((2^(k+1)-1)/2) == C(N) == O C(N)  
  
# 02/11/20
Breadth First Search works with queue by queueing the values and popping once the value is compared   
Ex. if a tree is 1 - 3 - 5  
				   \ 4 - 6  
				   	   \ 7    
	Goal is 6
This would queue 1 (1) then 3 (pop 1) then 4 (pop 3) then 5 (pop 4) then 6 (pop 5, found)  

# 02/18/20
### Trees  
Trees give Log(n) complexity usually, its a connected graph with no cycles  
Depth of tree makes the complexity  
Height is how many nodes long from root to base   
Height of vertex is distance to certain node  
Methods of traversal:  
1. Preorder traversal    
	* V-LS-RS
2. Postorder traversal      
	* LS-RS-V
3. Levelorder traversal     
	* Only one that is breath-first  
	* Top down, left to right
4. In order traversal (only for Binary trees)  
	* LS-v-RS  
**Printing order will be on test**   
Binary tree is a tree with each parent only having *two* node children  
Example:   
```  
struct BinaryNode {  
	Object element;  
	BinaryNode *left;  
	BinaryNode *rigth;
}    
```    
A **Complete Binary Tree** has all nodes, except the bottom level, at the max of two children for each parent node (the bottom nodes can have one node but it must be in the leftmost spots consecutively, Full Binary Tree is two nodes on every level)  
For a Complete Binary Tree storing level order is best (top down and left to right) so that logical jumps can be made to jump to certain locations in the arrays  
**Navigating Complete Binary Tree**
Navigating to parent of v[k] = v[(k - 1) / 2]    
Left child of v[k] = v[2 * k + 1]  
Right child of v[k] = v[2 * k + 2]  
Tree can be used as an expression tree to deal with order of operations, this is done by a binary tree of expressions and each bottom node being put in parenthesis and then pulled up a level where another parenthesis is added  
  
# Midterm Review    
[Top of Notes](#top)
### Intro  
All logs are base 2 unless specified   
**Arithmetic Review**  
### Recursion  
Each time a recursive function is called overhead is created with *function calls* and *activation records*  
Normally recursive break can be done by *if (x == 0) return 0;*  
When creating recursive functions make sure that:  
1. Define a base case, or where the program will terminate  
2. Create a case that will continually increment to the base case  
(for cleaner code)  
3. Assume all recursive calls work  
4. Don't duplicate work by making recursive calls twice  
Example (recursive fibonacci):   
```  
long fib(int k) {  
	if (x == 0 || x == 1) return 1;  
	return fib(k - 1) + fib(k - 2);
}    
```      
### Classes  
Define characteristics of types of things:  
* Thing's characteristics (attributes and methods)  
* What it can do (behaviors or methods)  
	* Properties and methods are called *members*  
	* Members can be data/variables/functions/methods  
Levels of hiding are *private*, *public*, and *protected*  
Initializer list- used to assign data directly to constructors  
Preprocessor commands are the `#ifndef HEADERNAME_H`, `#define HEADERNAME_H` and `#endif` at the end of the header (protects against multiple inclusions of header file)  
Interface is usually the raw .h file while implementation is the .hpp file since this is where functions declared in the header are given their uses   
:: is the scope resolution operator and used to identify the parts of classes  
Should always use string or vector data types except when optimizing code for speed, built-in data types can lead to more errors and programming  
In C++11:  
* Vectors can be initialized by curly braces for the elements in the vector {12, 13, 14}, or by parentheses for size of vector (12) vector of 12 in size  
* Range based for loops:  
```  
int sum = 0;  
for (int x:squares) {  
	sum += x;  
}  
```    
* Keyword *auto* (can detect what and how data types should be used and initialized    
**L-value, R-value, and References**  
L-value  
* Associated with non-temporary objects  
R-value  
* Associated with temporary objects that will be destroyed soon  
**Five special functions provided in C++ classes**  
1. Destructor     
	* Used to delete objects when they fall out of scope  
	* delete key word is almost always used  
	* Declared by `ObjName::~ObjName() {}`  
```    
~ObjName()   
{delete storedValue;}
```  
2. Copy constructor  
	* Copy if existing object is an lvalue  
	* Used by `ObjName x = a;` (if previously initialized and not declared but later uses = that is assignment operator)  
	* Both `ObjName(const ObjName &rhs)` and `ObjName(ObjName &&rhs)`  
```  
ObjName(const ObjName &rhs)  
{storedValue = new int{*rhs.storedValue};}
```  
3. Move constructor //since C++11    
	* Copy if existing object is an rvalue
	* Used by `ObjName x {a}` (if previously initialized and not declared but later uses = that is assignment operator)
	* Both `ObjName(const ObjName &rhs)` and `ObjName(ObjName &&rhs)`  
```  
ObjName(ObjName &&rhs) :storedValue{rhs.storedValue}  
{rhs.storedValue = nullptr;}
```  
4. Copy assignment operator=    
	* Only called when both LHS and RHS objects have been created  
	* Is called if RHS is lvalue  
	* `ObjName& operator=(const ObjName &rhs)`
```  
ObjName& operator=(const ObjName &rhs) {  
if (this != &rhs)  
	*storedValue = *rhs.storedValue;  
return *this;
}  
```  
5. Move assignment operator= //since C++11      
	* Only called when both LHS and RHS objects have been created  
	* Is called if RHS is rvalue
	* `ObjName& operator=(ObjName &&rhs)`  
```  
ObjName& operator=(ObjName &&rhs) {  
	std::swap(storedValue, rhs.storedValue);  
	return *this;
}  
```  
Similarly, a default constructor will be created only if no constructor was created manually  
**Templates**  
Used to create generic functions and classes that work with multiple data types  
Uses `template <typename TempName>` to pass TempName as any data type that is passed  
### Algorithm Analysis  
Count the number of operations, and how fast time increments as input size approaches infinity  
### Big O Explanation  
Focuses on finding how the runtime grows of the function as it's input size approaches infinity?  
When given the time it takes for functions to complete all you need to do is:  
1. Find the fastest growing term  
2. Remove the coefficient   
Ex. if T = dn² + cn + e = O(n²)  
Usually just count arithmetic terms used and reason through how long each command will take to complete and add all the times up to reach a O(Nth term)  
**Containers**
Sequence Containers/pContainer are positional containers that support access to elements with C<T>::iterator    
Examples of pContainers are vectors, lists, stacks, queue, and deque  
Deque (Double Ended Queue) can be accessed from the front or back end   
Deque operations:  
* push\_front, pop\_front, front, push\_back, pop\_back, back all are *O(1)*  
* Size is *O(size/n)*  
* Time and space for iterator operations are O(1)  
Most pContainers natively support begin() and end() to get the iterator positions at beginning and end of containers  
### ADT's 
An ADT (Advanced Data Types) are objects that are a collection of data as well as have supported operations for accessing and operating on data and subsets of data  
Generally supported by any ADT's, iterators are used to store memory locations of data points that can be incremented and acted upon like ints  
Often one wants to use auto data type if working within C++11 for iterators   
### Lists  
Two main types are (both head/tail point to null at the beginning and end of the list, empty list means head and tail point to each other):  
* Singly Linked list    
	* Connected by pointer to the next item
* Doubly Linked list  
	* Connected by pointer to item before it and after it   
### Stacks and Queues  
Stacks are:  
* LIFO  
* Used in:  
	* Depth first searches  
	* Backtracking
	* Evaluating postfix expressions    
	* Converting infix to postfix  
	* Function calls (computer stack with function calls)  
	* Recursion  
Depth First Search goes down each branch of a struct until it can't first and pushes nodes onto stack, if value matches stack contains path to it if not stack is popped until node with possibility of moving down  
```  
DFS() {  
	stack<location> S;  
	S.push(start);  
	while(!S.empty()){  
		t = S.top();  
		if (t == goal) Success(S);  
		if (//univisted neighbors) {  
			//Choose unvisited neighbors and mark them visited  
			S.push(n);
		}    
		else {  
			BackTrack(S);
		}  
	}  
	Failure(S);
}      
BackTrack(S) {  
	while(!S.empty() && S.top() has no unvisted neighbors)  
			S.pop();
}    
Success(S) {  
	while(!S.empty()) {  
		output(S.top());
		S.pop();
	}  
}    
Failure(S) {  
	while(!S.empty())  
		S.pop();
}  
```    
**Infix and Postfix**  
Look at s-notes  
**Queue**  
* FIFO  
* Used in:  
	* Buffers  
	* Breadth first search  
	* Simulations  
	* Producer-consumer Problems  
Breadth First Search- goes out by looking at **two** direct children nodes and if not goal pops parent and pushes children making neighbor the next node to evaluate  
```  
BFS() {  
	queue<location> Q;  
	Q.push(start);  
	while (Q is not empty) {  
		t = Q.front();
			for (each unvisited neighbor n of node t) {  
				Q.push(n);  
				if (n == goal) Success(S);
			}  
	}  
}  
```    
### Sets and Maps  
Both Sets and Maps are **Associative Containers/aContainers**  
Data in these are not accessed by memory location but instead by *value*  
Supports bidirectional iterators (++ or --)  
Multimodal vs Unimodal  
Multimodal- support duplicate information, insertions always increase size by 1  
Unimodal- duplicate elements are not allowed, inserts have dual functionality (if not in C insert V, if V is in C overwrite existing V)  
Pair data types- Can hold two *different kinds of data* that are kept tied to each other  
Set:  
* A sorted associative container that *does not* allow duplicates  
* Stores objects  
* *Unimodal*  
MultiSet  
* A sorted associative container that allows duplicates   
* Stores objects  
* Multimodal  
* AKA bags  
Maps:  
* Store values as a *key* and *data*  
* Sorted according to the keys  
* Unimodal  
* AKA table, associative array  
MultiMap:  
* Store values as a *key* and *data*  
* Sorted according to the keys  
* Multimodal  
### Tree  
Type of data structure that has a unique parent for each node existing and has a root (leaves, or leaf, are nodes without children nodes)  
Root is at depth 0, depth goes from 0 to each level incrementing by 1, level x is the depth of the node found  
Height is distance to root  
Different tree traversal methods are:  
* Preorder traversal    
	* Checks each child node first then traverses back up the tree  
	* Depth first search (possibly stack based)  
	* Visits on arrival  
	* **Vertex, left subtree, right subtree**
* Postorder traversal    
	* Checks each child node and compares then moves down
	* Depth first search (possibly stack based)  
	* Visits on departure    
	* **Left subtree, right subtree, vertex**
* Levelorder traversal  
	* Visits two children node and finishes nodes on the same level before moving down (possibly queue based)  
	* Visits on departure      
	* **Vertex, Left child, right child**
* Inorder traversal  
	* Looks at left child vertex then right child   
	* Follows left path to the max then traverses back and right path
	* **Left subtree, vertex, right subtree**
**Binary Trees** Trees with only 2 nodes at max  
**Complete Binary Trees** Binary Trees with all nodes maxed at two and data in each  
**Review above section on trees and traversal of trees**  
*AVL(Adelson-Velskii and Landis) Trees*  
  
# Data Structures Notes (video)    
For complexity analysis try and count max number of times a loop
### Singly and Doubly Linked List
List is a sequential node that points to another node containing pointers and data, last node points to Null *always*  
Can be used for list, queue, stacks, circular list (last node points to first), hash tables  
*Head* is the first node always, contains data and pointer to next node  
*Tail* is the last node that points to null  
A node is usually a struct containing pointers and data  
Singly point only to next node vs Doubly point links to next and last node  
Singly provides:  
* Less memory use  
* Simpler to implement  
* But cannot easily access last elements  
Doubly provides:  
* Can be traversed backwards  
* Takes double the memory  
**Complexity Analysis of Linked Lists**:  
Singly Linked List    
* Search- O(n)  
* Insert at head- O(1)  
* Insert at tail- O(1)  
* Remove at head- O(1)  
* *Remove at tail- O(n)*  
* Remove at middle- O(n)
Doubly Linked List
* Search- O(n)  
* Insert at head- O(1)  
* Insert at tail- O(1)
* Remove at head- O(1)  
* *Remove at tail- O(1)*  
* Remove at middle- O(n)  
  
### Stacks  
LIFO  
Uses push and pop to add and remove from stack  
**Complexity analysis of Stacks**:  
* Pushing- O(1)  
* Popping- O(1)   
* Peeking- O(1)  
* Searching- O(n)  
* Size- O(1)  
  
### Queue   
FILO  
Enqueue and dequeue are used to add items to the back and pop from the front  
Used for *breadth first search* graph traversal  
*Complexity analysis of a queue*:  
* Enqueue- O(1)  
* Dequeue- O(1)  
* Peeking- O(1)  
* Contains- O(n)  
* Removal- O(n)  
* Is empty- O(1)  
**Breadth First Search** starts at node and visits neighbors adding them to the queue and then visits neighbors of each as they are added    
Done by:  
```  
Q is the queue  
Q.enqueue(startingNode)  
StartingNode.visited = true
while Q is not empty Do    
	node = Q.dequeue()  
	for neighbor in neighbors(node):  
		if neighbor has not been visited:  
			neighbor.visited = true  
			Q.enqueue(neighbor)
```    
**Priority Queue**  
Same as queue but priority is assigned to values so that there is kept track which items to print first, need to be *comparable data so that it can be ordered and given priority*  
*poll()* means remove item with highest priority  
*add(item)* adds item with item value to priority queue   
*poll rest* grabs everything else in the queue with the immediate next value being the lowest automatically  
Uses heap to assign priority automatically  
**Heap** is a tree based data structure that sorts based off two structures  
**Max Heap**  
* Root of tree is the max value and children are less then throughout the tree  
* If root is 8 following children could be 7 and 6 then 7 children could be 4 and 5 and 6 children could be 4 and 5
* Doesn't have to be a binary tree
**Min Heap**      
* Root of tree is the smallest value and children are greater then throughout the tree
* If root is 0 following children could be 1 and 2 then 1 children could be 3 and 4 and 2 children could be 4 and 5
* Doesn't have to be a binary tree  
**Complexity Analysis of Priority Queue**:  
* Binary Heap Construction- O(n)  
* Polling- O(log(n))  
* Peeking- O(1)  
* Adding- O(log(n))  
* Naive Removing (removing non root)- O(n)  
* Advanced removing with help from hash table- O(log(n))  
* Naive Contains- O(n)  
* Contains check with help of hash table- O(1)  
  
### Trees  
**Binary Tree/Binary Search Tree**  
A tree is an undirected graph which satisfies the following:  
* An acyclic connected graph  
* A connected graph with N nodes and N-1 edges  
* A graph in which any two vertices are connected by *exactly* one path    
![Tree example](./Midterm/photos/tree.png)  
Rooted tree is the top most node of the tree, when initializing setting a root never matters   
A *child* is the node that branches from the parent, while the *parent* is the base that nodes extend from   
Root node can have either itself as the parent or null  
Practical example: parent of root directory on Linux is itself so that `cd ..` at root returns back still to the root folder  
A **Binary Tree** is a tree where every node has at most 2 children  
A **Binary Search Tree** is a binary tree that makes sure the left subtree is less than the right subtree while the parent must be between the two nodes    
**Complexity Analysis of BST**:  
* Insert- O(log(n)), O(n) worst case  
* Delete- O(log(n)), O(n) worst case  
* Remove- O(log(n)), O(n) worst case  
* Search- O(log(n)), O(n) worst case  
When inserting into BST need to ensure data type is comparable and check for 4 cases **after starting at the root**:  
1. Check if less than (step down the left side of tree)  
2. Check if greater than (step down the right side of tree)  
3. Check if equal (meaning duplicate)  
4. If all above pass, meaning farthest down in tree and where it should be but it doesn't exist then create the new node  
For BST only reason it **can** be linear is if every value is being added to one side every time, like adding 1 2 3 4 5 6 would all be being added in a line meaning that it would iterate each time over each element   
![Example of worst case](./Midterm/photos/bstWorstCase.png)  
For finding in a BST -1 can tell it is on the left subtree, 1 if it is on the right, and 0 if found (meaning return the current node)  
**Preorder**  
```  
preorder(node) {  
	if node == null: return 
	print(node.value);  
	preorder(node.left)  
	preorder(node.right)
}  
```      
![Preorder](./Midterm/photos/preorder.png)
**Inorder**  
```  
inorder(node){  
	if node == null: return  
	inorder(node.left)  
	print(node.value)  
	inorder(node.right)  
}    
```      
![Inorder](./Midterm/photos/inorder.png)
**Postorder**  
```  
postorder(node) {  
	if node == null: return  
	postorder(node.left)  
	postorder(node.right)  
	print(node.value)
}    
```          
When being used on BST values are printed **in order**
![Postorder](./Midterm/photos/postorder.png)
**Level order**  
Goes in order by printing what's on each level of the tree, uses **breadth first search (queue)**  
![Level Order](./Midterm/photos/levelOrder.png)  
### Balanced Binary Search Tree and AVL Trees
**Balanced Binary Search Tree**- Conforms to normal Binary Tree rules but also are self-balancing where the tree will adjust to maintain the minimum height it can achieve  
**Complexity Analysis of BBST**:  
* Insert- O(log(n))
* Delete- O(log(n))
* Remove- O(log(n))
* Search- O(log(n))  
They use the concept *Tree Rotation* to ensure balancing trees, two kinds:  
1. Tree Invariant- Rule that ensures trees are balanced  
2. Tree Rotations    
	* Still maintains BST where numbers are still ordered except the root node is changed and the tree is altered to maintian 2 children nodes  
	* Often trees can have references to their parent node as well as two children (like doubly linked list), but when rotating these 6 changes need to be made instead of 3
![BBST Rotations](./Midterm/photos/bbstRotation.png)  

[Top of midterm review](#midterm-review)
