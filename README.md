class SinglyLinkedList:
    class Node:
        def __init__(self, student_id, name, age):
            self.student_id = student_id
            self.name = name
            self.age = age
            self.next = None

    def __init__(self):
        self.head = None

    def insert(self, student_id, name, age):
        new_node = self.Node(student_id, name, age)
        new_node.next = self.head
        self.head = new_node
        print(f"Inserted student {name} with ID {student_id} into Singly Linked List.")

    def delete(self, student_id):
        current = self.head
        previous = None
        while current:
            if current.student_id == student_id:
                if previous:
                    previous.next = current.next
                else:
                    self.head = current.next
                print(f"Deleted student {current.name} with ID {student_id} from Singly Linked List.")
                return
            previous = current
            current = current.next
        print(f"Student with ID {student_id} not found in Singly Linked List.")

    def display(self):
        current = self.head
        while current:
            print(f"ID: {current.student_id}, Name: {current.name}, Age: {current.age}")
            current = current.next
        if self.head is None:
            print("No students in Singly Linked List.")

class DoublyLinkedList:
    class Node:
        def __init__(self, student_id, name, age):
            self.student_id = student_id
            self.name = name
            self.age = age
            self.next = None
            self.prev = None

    def __init__(self):
        self.head = None

    def insert(self, student_id, name, age):
        new_node = self.Node(student_id, name, age)
        new_node.next = self.head
        if self.head is not None:
            self.head.prev = new_node
        self.head = new_node
        print(f"Inserted student {name} with ID {student_id} into Doubly Linked List.")

    def delete(self, student_id):
        current = self.head
        while current:
            if current.student_id == student_id:
                if current.prev:
                    current.prev.next = current.next
                if current.next:
                    current.next.prev = current.prev
                if current == self.head:
                    self.head = current.next
                print(f"Deleted student {current.name} with ID {student_id} from Doubly Linked List.")
                return
            current = current.next
        print(f"Student with ID {student_id} not found in Doubly Linked List.")

    def display(self):
        current = self.head
        while current:
            print(f"ID: {current.student_id}, Name: {current.name}, Age: {current.age}")
            current = current.next
        if self.head is None:
            print("No students in Doubly Linked List.")

class CircularLinkedList:
    class Node:
        def __init__(self, student_id, name, age):
            self.student_id = student_id
            self.name = name
            self.age = age
            self.next = None

    def __init__(self):
        self.head = None

    def insert(self, student_id, name, age):
        new_node = self.Node(student_id, name, age)
        if self.head is None:
            self.head = new_node
            new_node.next = self.head
        else:
            temp = self.head
            while temp.next != self.head:
                temp = temp.next
            temp.next = new_node
            new_node.next = self.head
        print(f"Inserted student {name} with ID {student_id} into Circular Linked List.")

    def delete(self, student_id):
        if self.head is None:
            print("List is empty.")
            return
        current = self.head
        previous = None
        while True:
            if current.student_id == student_id:
                if previous is not None:
                    previous.next = current.next
                else:
                    temp = self.head
                    while temp.next != self.head:
                        temp = temp.next
                    temp.next = current.next
                    self.head = current.next
                print(f"Deleted student {current.name} with ID {student_id} from Circular Linked List.")
                return
            elif current.next == self.head:
                break
            previous = current
            current = current.next
        print(f"Student with ID {student_id} not found in Circular Linked List.")

    def display(self):
        if self.head is None:
            print("List is empty.")
            return
        temp = self.head
        while True:
            print(f"ID: {temp.student_id}, Name: {temp.name}, Age: {temp.age}")
            temp = temp.next
            if temp == self.head:
                break

class Stack:
    def __init__(self):
        self.stack = []

    def add(self, student_id, name, age):
        self.stack.append((student_id, name, age))
        print(f"Added student {name} with ID {student_id} to stack.")

    def delete(self):
        if not self.stack:
            print("Stack is empty.")
        else:
            student = self.stack.pop()
            print(f"Deleted student {student[1]} with ID {student[0]} from stack.")

    def is_full(self):
        print("Stack can grow dynamically in Python, so it's never full.")

    def is_empty(self):
        print("Stack is empty." if not self.stack else "Stack is not empty.")

    def display(self):
        print("Stack contents:")
        for student in self.stack:
            print(f"ID: {student[0]}, Name: {student[1]}, Age: {student[2]}")

class Queue:
    def __init__(self):
        self.queue = []

    def enqueue(self, student_id, name, age):
        self.queue.append((student_id, name, age))
        print(f"Enqueued student {name} with ID {student_id} into queue.")

    def dequeue(self):
        if not self.queue:
            print("Queue is empty.")
        else:
            student = self.queue.pop(0)
            print(f"Dequeued student {student[1]} with ID {student[0]} from queue.")

    def is_full(self):
        print("Queue can grow dynamically in Python, so it's never full.")

    def is_empty(self):
        print("Queue is empty." if not self.queue else "Queue is not empty.")

    def display(self):
        print("Queue contents:")
        for student in self.queue:
            print(f"ID: {student[0]}, Name: {student[1]}, Age: {student[2]}")

class BinaryTree:
    class Node:
        def __init__(self, student_id, name, age):
            self.student_id = student_id
            self.name = name
            self.age = age
            self.left = None
            self.right = None

    def __init__(self):
        self.root = None

    def insert(self, student_id, name, age):
        if self.root is None:
            self.root = self.Node(student_id, name, age)
        else:
            self._insert(self.root, student_id, name, age)

    def _insert(self, node, student_id, name, age):
        if student_id < node.student_id:
            if node.left is None:
                node.left = self.Node(student_id, name, age)
            else:
                self._insert(node.left, student_id, name, age)
        else:
            if node.right is None:
                node.right = self.Node(student_id, name, age)
            else:
                self._insert(node.right, student_id, name, age)

    def preorder(self, node):
        if node:
            print(f"ID: {node.student_id}, Name: {node.name}, Age: {node.age}")
            self.preorder(node.left)
            self.preorder(node.right)

    def postorder(self, node):
        if node:
            self.postorder(node.left)
            self.postorder(node.right)
            print(f"ID: {node.student_id}, Name: {node.name}, Age: {node.age}")

    def inorder(self, node):
        if node:
            self.inorder(node.left)
            print(f"ID: {node.student_id}, Name: {node.name}, Age: {node.age}")
            self.inorder(node.right)

# Main program loop
while True:
    print("\n\n               \"Student Management System\"            ")
    print("Press 1 For Singly Linked List")
    print("Press 2 For Doubly Linked List")
    print("Press 3 For Circular Linked List")
    print("Press 4 For Stack")
    print("Press 5 For Queue")
    print("Press 6 For Binary Tree")
    print("Press 7 To Exit")
    choice = int(input("\nEnter your choice: "))

    match choice:
        case 1:
            sll = SinglyLinkedList()
            while True:
                print("\nPress 1 to Add a student in Singly Linked List")
                print("Press 2 to Remove a student in Singly Linked List")
                print("Press 3 to Display students in Singly Linked List")
                print("Press 4 to Go back")
                c = int(input("\nEnter your choice: "))
                if c == 1:
                    student_id = int(input("Enter student ID: "))
                    name = input("Enter student name: ")
                    age = int(input("Enter student age: "))
                    sll.insert(student_id, name, age)
                elif c == 2:
                    student_id = int(input("Enter student ID to remove: "))
                    sll.delete(student_id)
                elif c == 3:
                    sll.display()
                elif c == 4:
                    break

        case 2:
            dll = DoublyLinkedList()
            while True:
                print("\nPress 1 to Add a student in Doubly Linked List")
                print("Press 2 to Remove a student in Doubly Linked List")
                print("Press 3 to Display students in Doubly Linked List")
                print("Press 4 to Go back")
                c = int(input("\nEnter your choice: "))
                if c == 1:
                    student_id = int(input("Enter student ID: "))
                    name = input("Enter student name: ")
                    age = int(input("Enter student age: "))
                    dll.insert(student_id, name, age)
                elif c == 2:
                    student_id = int(input("Enter student ID to remove: "))
                    dll.delete(student_id)
                elif c == 3:
                    dll.display()
                elif c == 4:
                    break

        case 3:
            cll = CircularLinkedList()
            while True:
                print("\nPress 1 to Add a student in Circular Linked List")
                print("Press 2 to Remove a student in Circular Linked List")
                print("Press 3 to Display students in Circular Linked List")
                print("Press 4 to Go back")
                c = int(input("\nEnter your choice: "))
                if c == 1:
                    student_id = int(input("Enter student ID: "))
                    name = input("Enter student name: ")
                    age = int(input("Enter student age: "))
                    cll.insert(student_id, name, age)
                elif c == 2:
                    student_id = int(input("Enter student ID to remove: "))
                    cll.delete(student_id)
                elif c == 3:
                    cll.display()
                elif c == 4:
                    break

        case 4:
            stack = Stack()
            while True:
                print("\nPress 1 to Add a student in Stack")
                print("Press 2 to Remove a student from Stack")
                print("Press 3 to Display students in Stack")
                print("Press 4 to Check if Stack is full")
                print("Press 5 to Check if Stack is empty")
                print("Press 6 to Go back")
                c = int(input("\nEnter your choice: "))
                if c == 1:
                    student_id = int(input("Enter student ID: "))
                    name = input("Enter student name: ")
                    age = int(input("Enter student age: "))
                    stack.add(student_id, name, age)
                elif c == 2:
                    stack.delete()
                elif c == 3:
                    stack.display()
                elif c == 4:
                    stack.is_full()
                elif c == 5:
                    stack.is_empty()
                elif c == 6:
                    break

        case 5:
            queue = Queue()
            while True:
                print("\nPress 1 to Add a student in Queue")
                print("Press 2 to Remove a student from Queue")
                print("Press 3 to Display students in Queue")
                print("Press 4 to Check if Queue is full")
                print("Press 5 to Check if Queue is empty")
                print("Press 6 to Go back")
                c = int(input("\nEnter your choice: "))
                if c == 1:
                    student_id = int(input("Enter student ID: "))
                    name = input("Enter student name: ")
                    age = int(input("Enter student age: "))
                    queue.enqueue(student_id, name, age)
                elif c == 2:
                    queue.dequeue()
                elif c == 3:
                    queue.display()
                elif c == 4:
                    queue.is_full()
                elif c == 5:
                    queue.is_empty()
                elif c == 6:
                    break

        case 6:
            tree = BinaryTree()
            while True:
                print("\nPress 1 to Add a student in Binary Tree")
                print("Press 2 to Display students in Preorder")
                print("Press 3 to Display students in Postorder")
                print("Press 4 to Display students in Inorder")
                print("Press 5 to Go back")
                c = int(input("\nEnter your choice: "))
                if c == 1:
                    student_id = int(input("Enter student ID: "))
                    name = input("Enter student name: ")
                    age = int(input("Enter student age: "))
                    tree.insert(student_id, name, age)
                elif c == 2:
                    tree.preorder(tree.root)
                elif c == 3:
                    tree.postorder(tree.root)
                elif c == 4:
                    tree.inorder(tree.root)
                elif c == 5:
                    break

        case 7:
            print("Exiting program.")
            break

        case _:
            print("\nInvalid choice, please select again.")
