#Binary Heaps

##Defination

	Binary max-heap is a binary tree where the value if each node is at least the values of its children.

## Basic Operations

	GetMax(): Find max value of binary heap O(1)

	Insert(val): insert the value val in binary heap O(height)

	ExtractMax(): extract the maximun value of the binary heap O(height)

	ChangePriority(it, p): changes the priority of an element pointed at it to p O(height)

	Remove(p): remove the element p O(height)

For the better implementation of the binary heap we use complete binary tree.
	A binary tree is called complete if all its levels are filled completely

### Advantage of complete binary tree to use as binary heap

	1) The height of any complete binary tree with n nodes is O( log(n) ).
	2) Can be stored as array
		For any iterator i:
			a) parent(i) = floor(i/2)
			b) leftchild(i) = 2*i
			c) rightchild(i) = 2i + 1

### General Setting

	maxSize: max no. of element in heap
	size: present size of heap
	H[maxsize]: array representing tree // 1 base index

## Implementation

### Parent(i)

	Parent(i) {
		return floor(i/2)
	}


### LeftChild(i)

	LeftChild(i) {
		return 2 * i
	}

### RightChild(i)

	RightChild(i) {
		return (2 * i) + 1
	}

### GetMax()

	GetMax() {
		return H[1]
	}

### SiftUp(i)

	SiftUp(i) {

		while i > 1 and H[Parent(i)] < H[i]:
			swap H[Parent(i)] and H[i]

		i = Parent(i)
	}

### ShiftDown(i)

	ShiftDown(i) {

		maxIndex = i
		l = LeftChild(i)

		if l <= size and H[l] > H[maxIndex]:
			maxIndex = l

		r = RightChild(i)

		if r <= size and H[r] > H[maxIndex]:
			maxIndex = r

		if i != maxIndex:
			swap H[i] and H[maxIndex]
			ShiftDown(maxIndex)
	}

### Insert(p)

	Insert(p) {

		if size = maxSize:
			return ERROR

		size = size + 1
		H[size] = p

		ShiftUp(size)
	}

### ExtractMax()

	ExtractMax() {

		result = H[1]
		H[1] = H[size]
		size = size -1

		ShiftDown(1)

		return result
	}

### Remove(i)

	Remove(i) {

		H[i] = infinity
		ShiftUp(i)
		ExtractMax()

	}

### ChangePriority(i, p)

	ChangePriority(i, p) {

		oldp = H[i]
		H[i] = p

		if p > oldp:
			ShiftUp(i)

		else:
			ShiftDown(i)
	}


## Time Complexity

	GetMax()             : O(1)
	Insert(p)            : O( log(n) )
	ExtractMax()         : O( log(n) )
	ChangePriority(i, p) : O( log(n) )
	Remove(i)            : O( log(n) )