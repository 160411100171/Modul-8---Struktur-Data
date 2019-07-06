# Modul-8---Struktur-Data
Binary Tree

Tree dalam Struktur Data

Salah Satu bentuk Struktur Data tidak linier Yang menggambarkan hubungan Yang bersifat hirarkis antara elemen-elemen. Tree Bisa didefinisikan sebagai kumpulan node dengan Satu elemen Khusus Yang disebut root. Dan Node lainnya terbagi menjadi Himpunan-Himpunan Yang tak saling berhubungan Satu sama lain (subtree). Istilah-istilah dalam tree :

•	Node, merupakan bagian dari tree yang menyimpan informasi atau juga disebut sebagai key.

•	Edge, yang menghubungkan antara node yang satu dengan yang lain. Hanya ada satu edge yang masuk ke dalam node, dan satu atau lebih edge yang keluar dari suatu node.

•	Root, node yang terletak di paling atas, tidak ada edge yang masuk ke dalam node root ini, tapi root mempunyai satu atau lebih dari satu edge yang keluar.

•	path, merupakan urutan node dari root sampai tujuan, misalkan computer --> D: --> Mata Kuliah --> Struktur Data

•	children, merupakan node-node yang memiliki edge yang masuk dari node yang sama. Misalkan program files, users, dan windows merupakan children, krn memiliki edge masuk yang sama-sama berasal dari node C:

•	Parent, node yang memiliki edge yang keluar dari node tersebut, misalkan node C: adalah parent dari program files, users, dan windows.

•	Siblings, adalah node-node yang berasal dari parent yang sama.

•	subtree, kumpulan dari node dan edge yang terdiri dari parent dan semua node setelah parent

•	leaf node, node yang tidak memiliki edge yang keluar, node yang tidak memiliki children

•	level, tingkatan dari node. Root merupakan level ke-0, semakin kebawah maka level dari node tersebut semakin besar, misalkan struktur data berada di level ke-3.

•	height, merupakan tinggi tree, nilai dari height ini adalah level maksimum dari tree.


-----------------------------------------------------------------------------------
Binary Tree dalam Struktur Data

Tree dengan syarat bahwa tiap node memiliki boleh maksimal dua subtree dan kedua subtree tersebut harus terpisah. Sesuai dengan definisi tersebut, maka tiap node dalam binary tree hanya boleh memiliki paling banyak dua child.

      class BinaryTree:
          def __init__(self, root):
              self.key = root
              self.leftChild = None
              self.rightChild = None

      myTree=BinaryTree(10)
      print(myTree.leftChild)

      >>>
      Running: None

Class BinaryTree ini harus memiliki dua method utama yaitu, insertLeft dan insertRight.

	class BinaryTree:
			def __init__(self, root):
			self.key = root
			self.leftChild = None
			self.rightChild = None
			def insertLeft(self, new_node):
			if self.leftChild == None:
					self.leftChild = BinaryTree(new_node)
			else:
					t = BinaryTree(new_node)
					t.leftChild = self.leftChild
					self.leftChild = t
			def insertRight(self, new_node):
			if self.rightChild == None:
					self.rightChild = BinaryTree(new_node)            
			else:
					t = BinaryTree(new_node)
					t.rightChild = self.rightChild
					self.rightChild = t

Berikut tambahan method pada class BinaryTree, untuk mendapatkan informasi mengenai left child, right child, dan root dari suatu binary tree.

	class BinaryTree:
			def __init__(self, root):
			self.key = root
			self.leftChild = None
			self.rightChild = None
			def insertLeft(self, new_node):
			if self.leftChild == None:           
					self.leftChild = BinaryTree(new_node)         
			else:
					t = BinaryTree(new_node)
					t.leftChild = self.leftChild
					self.leftChild = t

			def insertRight(self, new_node):
			if self.rightChild == None:
					self.rightChild = BinaryTree(new_node)            
			else:
					t = BinaryTree(new_node)
					t.rightChild = self.rightChild
					self.rightChild = t

			def getRightChild(self):
			return self.rightChild
			def getLeftChild(self):
			return self.leftChild
			def setRootVal(self, obj):
			self.key = obj
			def getRootVal(self):
			return self.key


-----------------------------------------------------------------------------------
Pharsing Binary Tree
Terdapat dua tahapan untuk menyelesaikan Persamaan Matematikan tersebut, dengan menggunakan Binary Tree, yaitu Pembentukan Parse Tree dan Evaluasi Persamaan Matematika

-----------------------------------------------------------------------------------
Pembentukan Parse Tree

Persamaan Matematika harus dipecah menjadi list token agar dapat dibuat menjadi parse tree. 

Token-token untuk persamaan Matematika tersebut antara lain:

•	Kurung buka, kurung buka ini menandakan ekspressi baru yang akan dioperasi, oleh karena itu perlu dibuat subtree baru untuk menyelesaikan ekspressi baru ini

•	kurung tutup, kurung tutup ini menandakan akhir dari ekspressi matematika

•	operand, operand ini yang akan jadi leaf node dan children dari operator

•	operator, operator merupakan parent dan punya left maupun right child

Algoritman Pembentukan Parse Tree

1.	Jika current token adalah kurung buka, '(' , tambahkan node baru sebagai left child dari current Node dan jadikan node baru ini sebagai current node

2.	jika current token adalah operator, set nilai key dari current node dengan operator tersebut. Tambahkan node baru sebagai right child dari current node, jadikan right child ini sebagai current node

3.	jika current token adalah operand, maka set nilai key dari current node dengan operand tersebut dan jadikan parent dari node tersebut menjadi current node

4.	jika current token adalah kurung tutup, ')', maka kembali ke parent dari current node

Binary tree class menyediakan method untuk menambah node baru baik sebelah kiri maupun kanan, dan menuju left child maupun right child. Method ini sangat diperlukan untuk pembuatan parse tree.

	///stack
	def stack():
			s=[]
			return (s)

	def push(s,data):
			s.append(data)

	def pop(s):
			data=s.pop()
			return(data)

	def peek(s):
			return(s[len(s)-1])

	def isEmpty(s):
			return (s==[])

	def size(s):
			return(len(s))

	///class
	class BinaryTree:
			def __init__(self, root):
			self.key = root
			self.leftChild = None
			self.rightChild = None
			def insertLeft(self, new_node):
			if self.leftChild == None:           
					self.leftChild = BinaryTree(new_node)         
			else:
					t = BinaryTree(new_node)
					t.leftChild = self.leftChild
					self.leftChild = t

			def insertRight(self, new_node):
			if self.rightChild == None:
					self.rightChild = BinaryTree(new_node)            
			else:
					t = BinaryTree(new_node)
					t.rightChild = self.rightChild
					self.rightChild = t

			def getRightChild(self):
			return self.rightChild
			def getLeftChild(self):
			return self.leftChild
			def setRootVal(self, obj):
			self.key = obj
			def getRootVal(self):
			return self.key

	///ParseTree
	def buildParseTree(mathExp):
			tokenList = mathExp.split()
			parentStack = stack()
			expTree = BinaryTree(' ' )
			push(parentStack,expTree)
			print(tokenList)
			currentTree = expTree
			for i in tokenList:

			if i == '(' :
					print('if 1', i)
					currentTree.insertLeft(' ' )
					push(parentStack,currentTree)
					currentTree = currentTree.getLeftChild()
			elif i not in [ '+' , '-' , '*' , '/' , ')' ]:
					print('if 2', i)
					currentTree.setRootVal(int(i))

					parent = pop(parentStack)
					currentTree = parent
			elif i in [ '+' , '-' , '*' , '/' ]:
					print('if 3', i)
					currentTree.setRootVal(i)
					currentTree.insertRight(' ' )
					push(parentStack,currentTree)
					currentTree = currentTree.getRightChild()
			elif i == ')' :

					currentTree = pop(parentStack)
			else:
					raise ValueError
			return expTree

	///Main
	pt = buildParseTree(' ( 3 + ( 4 * 5 ) ) ')

	>>>
	Running: ['(', '3', '+', '(', '4', '*', '5', ')', ')']
		 if 1 (
		 if 2 3
		 if 3 +
		 if 1 (
		 if 2 4
		 if 3 *
		 if 2 5

	print(pt.getRootVal())
	tmp=pt.getLeftChild()
	print(tmp.getRootVal())

	>>>
	Running: +
		 3	

	if pt.getLeftChild():
		print('Tree')

	>>>
	Running: Tree

-----------------------------------------------------------------------------------
Evaluasi Persamaan Matematika

Penyelesaian persamaan matematika dengan menggunakan binary tree, diperlukan penyelesaian terlebih dahulu secara rekursif subtree dari binary tree tersebut. Untuk membuat fungsi rekursif, base case dari fungsi rekursif tersebut harus ditentukan terlebih dahulu.

Base case untuk penyelesaian persamaan matematika dengan binary tree secara rekursif adalah pada saat berada di leaf node.

Rekursif dilakukan dengan cara mengoperasikan left child dan right child dengan operator yang sesuai.

	import operator
	def evaluate(parse_tree):
			opers = { '+' :operator.add, '-' :operator.sub, '*' :operator.mul,'/' :operator.truediv}
			left = parse_tree.getLeftChild()
			right = parse_tree.getRightChild()
			if left and right:
			fn = opers[parse_tree.key]
			return fn(evaluate(left),evaluate(right))
			else:
			return parse_tree.key

	evaluate(pt)

	>>>
	Running: 23

-----------------------------------------------------------------------------------
Praktikum - Modul Binary Tree

Buatlah fungsi untuk membangun sebuah binary tree (Gunakan class Binary Tree yang telah dibuat)
yang merepresentasikan operasi matematika postfix, seperti contoh berikut :

Operasi matematika : 2 8 9 + *

Algoritma untuk membangun binary tree tersebut adalah :1

1. Jika token adalah sebuah operand, maka :

	a. Buat tree, dengan node (root) adalah operand tersebut

	b. Masukkan tree ke dalam stack

2. Jika token adalah operator, maka :

	a. Pop dua buah tree teratas (misal B dan C)

	b. Buat tree baru (misal A) dengan root node adalah operator

	c. Set B menjadi right child dari A

	d. Set C menjadi left child dari A

	e. Push tree yang terbentuk ke dalam stack

Tambahkan fungsi evaluate yang sudah dibuat sebelumnya di dalam kelas (untuk mengoperasikan binary tree yang sudah dibangun).

Perintah untuk eksekusi :

	a='2 8 9 + *'
	resTree=buildTree(a)
	evaluate(resTree)

Contoh hasil eksekusi :

	a='2 8 9 + *'
	resTree=buildTree(a)
	evaluate(resTree)
	>>>
	Running: 34

Contoh hasil eksekusi :

	a='2 4 + 3 5 * -'
	resTree=buildTree(a)
	evaluate(resTree)
	>>>
	Running: -9

	a='10 3 2 12 + - *'
	resTree=buildTree(a)
	evaluate(resTree)
	>>>
	Running: -110

-----------------------------------------------------------------------------------
Jawaban

	def main():
	    pass

	if __name__ == '__main__':
	    main()

	import operator
	class Stack:
	     def __init__(self):
		 self.items = []

	     def isEmpty(self):
		 return self.items == []

	     def push(self, item):
		 self.items.append(item)

	     def pop(self):
		 return self.items.pop()

	     def peek(self):
		 return self.items[len(self.items)-1]

	     def size(self):
		 return len(self.items)
	class BinaryTree:
	    def __init__(self,rootObj):
		self.key = rootObj
		self.leftChild = None
		self.rightChild = None

	    def insertLeft(self,newNode):
		if self.leftChild == None:
		    self.leftChild = BinaryTree(newNode)

		else:
		    t = BinaryTree(newNode)
		    t.leftChild = self.leftChild
		    self.leftChild = t


	    def insertRight(self,newNode):
		if self.rightChild == None:
		    self.rightChild = BinaryTree(newNode)

		else:
		    t = BinaryTree(newNode)
		    t.rightChild = self.rightChild
		    self.rightChild = t




	    def getRightChild(self):
		return self.rightChild

	    def getLeftChild(self):
		return self.leftChild

	    def setRootVal(self,obj):
		self.key = obj

	    def getRootVal(self):
		return self.key



	def buildParseTree(fpexp):
	    fplist = fpexp.split()
	    pStack = Stack()
	    eTree = BinaryTree('')
	    pStack.push(eTree)
	    currentTree = eTree
	    for i in fplist:
		if i == '(':
		    currentTree.insertLeft('')
		    pStack.push(currentTree)
		    currentTree = currentTree.getLeftChild()
		elif i not in ['+', '-', '*', '/', ')']:
		    currentTree.setRootVal(int(i))
		    parent = pStack.pop()
		    currentTree = parent
		elif i in ['+', '-', '*', '/']:
		    currentTree.setRootVal(i)
		    currentTree.insertRight('')
		    pStack.push(currentTree)
		    currentTree = currentTree.getRightChild()
		elif i == ')':
		    currentTree = pStack.pop()
		else:
		    raise ValueError
	    return eTree

	def postfix(tree):
	    if tree != None:
		postfix(tree.getLeftChild())
		postfix(tree.getRightChild())
		print(tree.getRootVal(), end=' ')

	def postfixreval(tree):
	    opers = {'+':operator.add, '-':operator.sub, '*':operator.mul, '/':operator.truediv}
	    res1 = None
	    res2 = None
	    if tree:
		res1 = postfixreval(tree.getLeftChild())
		res2 = postfixreval(tree.getRightChild())
		if res1 and res2:
		    return opers[tree.getRootVal()](res1,res2)
		else:
		    return tree.getRootVal()

	pt = buildParseTree("( ( 8 + 9 ) * 2 )")

	postfix(pt)
	print()
	print(postfixreval(pt))
