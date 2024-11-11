NAME: Omar Ahmed Hussein
ID: C1220299

import java.util.Arrays;

public class Assignment<T> {
    private  static  final  int capacity=2;
    private int top;
    private T[]  stack;


    Assignment(){
        this(capacity);

    }
    Assignment(int size){
        top=0;
        stack = (T[]) new Object[size];

    }


    boolean Empty(){
        return top==0;
    }

    int size(){
        return  top;
    }
    void push(T element){
        if( IFull());
        expand();
        stack[top]=element;
        top++;
    }

    public void expand(){
        stack= Arrays.copyOf(stack,stack.length * 2);
    }

    @Override
    public String toString() {
        return "StackArray{" +
                "top=" + top +
                ", stack=" + Arrays.toString(stack) +
                '}';
    }

    T peak(){
        if(Empty());
        return stack[top-1];

    }
    T pop(){
        if(Empty());
        top--;
        T removed= stack[top];
        stack[top]=null;
        stack[top]=null;
        return  removed;

    }

    boolean IFull(){
        return top==stack.length;
    }
    void display() {
        if(Empty() ){
            System.out.println("Is Empty");

        }
        for(int i=top-1; i>=0; i--) {
            System.out.println(stack[i]);
        }


    }


    private boolean RomoveDuplicate(T element) {
        if (size() == 0) {
            return false;
        }
        for (int i = 0; i <size(); i++) {
            if (stack[i] == element) {
                return true;
            }
        }
        return false;
    }



    public void merge(Assignment<T> arr1, Assignment<T> arr2) {
        int newSize = arr1.size() + arr2.size();


        if (stack.length < newSize) {
            stack = Arrays.copyOf(stack, newSize);
        }

        for (int i = 0; i < arr1.size(); i++) {
            boolean duplicated;
            duplicated = RomoveDuplicate( arr1.stack[i]);
            if (!duplicated)
                push(arr1.stack[i]);
        }

        for (int i = 0; i < arr2.size(); i++) {
            boolean duplicated;
            duplicated = RomoveDuplicate( arr2.stack[i]);
            if (!duplicated)
                push(arr2.stack[i]);
        }
    }




    public static void main(String[] args) {
        Assignment<String> list1=new Assignment<>(3);
        Assignment<String> list2=new Assignment<>(4);
        Assignment<String> list3=new Assignment<>();
        list1.push("Mohamed");
        list1.push("Ali");
        list1.push("Nor");
        ;

        list2.push("Omar");
        list2.push("Ahmed");
        list2.push("Hussein");

        list3.merge(list1,list2);


        list3.display();


    }

}
