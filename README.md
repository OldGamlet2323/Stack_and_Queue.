# Stack_and_Queue.

# Stack 
    public class Stack {

    private int top;
    private int capacity;
    private int[] storage;
    public Stack(int capacity) {
        this.capacity = capacity;
        top = -1;
        storage = new int[capacity];
    }
    
    public boolean push(int element){
        if(isFull()){
            System.out.println("Stack overflow");
            return false;
        }
        top++;
        storage[top] = element;
        return true;
    }
    
    public int pop(){
        if(isEmpty()){
            System.err.println("Stack underflow");
        }
        top--;
        return storage[top];
    }
    
    public int peek(){
        if( top < 0){
            System.err.println("Stack underflow");
            return -1;
        }
        return storage[top];
    }
    
    public int size(){
        return top + 1;
    }

    public boolean isFull(){
        if( top == storage.length - 1){
            System.err.println("This stack is full");
        }
        return top == capacity - 1;
    }

    public boolean isEmpty(){
        if(top == -1){
            System.err.println("Stack is empty");
        }
        return top == -1;
    }

    @Override
    public String toString() {
        StringBuilder sb= new StringBuilder();
        if(!isEmpty()){
            sb.append("Top: ");
            for(int i = top; i >= 0 ; i--){
                sb.append(storage[i]);
                if(i > 0){
                    sb.append(", ");
                }
            }
        }
        return sb.toString();
    }

# Queue

    public class Queue {
    private int front;
    private int rear;
    private int capacity;
    private int[] elements;
    private int size;

    public Queue(int capacity) {
        this.capacity = capacity;
        elements = new int[capacity];
        rear = -1;
        front = -1;
    }

    public void enqueue(int new_elements){
        if(size == capacity){
            System.err.println("Queue is full");
        }
        rear++;
        elements[rear] = new_elements;
        size++;
    }
    public int dequeue(){
        if (size == 0){
            System.err.println("Queue is empty");
        }
        front++;
        int deElements = elements[front];
        size--;
        return deElements;
    }

    public int getSize() {
        return size;
    }

    public int peek(){
            if(size == 0){
                System.err.println("Queue is empty. Cannot peek");
                return -1;
            } else if(size == capacity){
                System.err.println("Queue is full. Cannot peek");
            }
            return elements[front+1];
    }

    @Override
    public String toString() {
        StringBuilder sb = new StringBuilder();
        if (size == 0) {
            return "Queue is empty.";
        } else {
            sb.append("Queue: ");
            for (int i = front + 1; i <= rear; i++) {
                sb.append(elements[i]);
                if (i < rear) {
                    sb.append(", ");
                }
            }
        }
        return sb.toString();
    }

# Circualr Queue

    public class Circular_Queue {
    private Node front;
    private Node rear;

    public Circular_Queue(){
            front = null;
            rear = null;
    }

    public void enQueue(int data){
        Node new_Node = new Node(data);
        if(rear == null){
            rear = new_Node;
            front = rear;
        } else {
            rear.next = new_Node;
            rear = new_Node;
            rear.next = front;
        }
    }

    public int deQueue(){
        if(front == null) {
            System.err.println("Empty Queue!!");
            return -1;
        } else {
            int poppedElement = front.data;
            front = front.next;
            rear.next = front;
            return poppedElement;
        }
    }

    public int peek(){
        int element = 0;
        if(front == null) {
            System.err.println("Queue is empty!!");
        } else {
            element = front.data;
            return element;
        }
        return element;
    }
    
    public void print(){
        if(front == null) {
            System.err.println("Queue is Empty!!");
        } else {
            while(front != rear) {
                System.out.print(front.data + " ");
                front = front.next;
            }
            System.out.println(rear.data);
        }
    }
    
    public class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;

    }
}


