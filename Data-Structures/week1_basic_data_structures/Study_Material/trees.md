# Trees

### Height(tree) 

	Height(tree) {
		if tree == nil:
			return 0;

		return 1 + max(Height(tree.left) + Height(tree.right));
	}

### Size(tree)

	Size(tree) {
		if tree == nil:
			return 0;

		return 1 + max(Size(tree.left) + Size(tree.right));
	}

### Pre_order_traversal(tree)

	Pre_order_traversal(tree) {

		if tree = nil:
			return

		///Operations///

		Pre_order_traversal(tree.left)
		Pre_order_traversal(tree.right)
	}

### Post_order_traversal(tree)

	Post_order_traversal(tree) {

		if tree = nil:
			return

		Pre_order_traversal(tree.left)
		Pre_order_traversal(tree.right)

		///Operations///
	}

### Breath_first_Level_traversal(tree)

	Breath_first_Level_traversal(tree) {

		if tree == nil:
			return

		Queu q
		q.Enqueue(tree)

		while not q.Empty() :
			node = q.Dequeue()

			///Operations///

			if node.left != nil:
				q.Enqueue(node.left)

			if node.right != nil:
				q.Enqueue(node.right)

	}


### In_Order_traversal(tree)
	
	// Mostly for binary Tree
	
	In_Order_traversal(tree) { 

		if tree == nil:
			return

		In_Order_traversal(tree.left)

		///Operations on element///

		In_Order_traversal(tree.right)
	}