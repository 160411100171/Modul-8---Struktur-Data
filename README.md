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


---------------------------------------------------------------------------------------------------------------------
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


Pharsing Binary Tree
Terdapat dua tahapan untuk menyelesaikan Persamaan Matematikan tersebut, dengan menggunakan Binary Tree, yaitu Pembentukan Parse Tree dan Evaluasi Persamaan Matematika

