# CORE-JAVA-FOUNDATOION

STATIC KEYWORD:

Static keyword can only be applied for variables and methods

a1) static variable

a2) static method

b1) non-static variable

b2) non-static method

**1. Static methods can access static stuff directly (without object).**

public class StaticAccessStatic {
    
    static int a = 10;

    static void m1() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {
        m1(); 
        System.out.println(a);
    }
}

**2. Static methods can access non-static stuff through object.**

public class StaticAccessNonStatic {
    
    int a=10;

    void m1() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {
        StaticAccessNonStatic s = new StaticAccessNonStatic();
        s.m1();
        System.out.println(s.a);
    }
}

**3. Non-static methods can access everything directly.**

public class NonStaticAccessAll {
    
    static int a = 30;
    int b = 40;

    void m1() {
        System.out.println(a);
        System.out.println(b);
        m2();
        m3();
    }

    static void m2()
    {
        System.out.println("This is m1 method");
    }

    void m3()
    {
        System.out.println("This is m2 method");
    }

    public static void main(String[] args) {
        NonStaticAccessAll obj = new NonStaticAccessAll();
        obj.m1();
    }
}

**Note:** if the main method is in different class then we should use classname.variablename and classname.methodname for static variable and method

**what is System.out.println();**

class Test // Test is a user define class

{

    static String s = "welcome"; // here String is a class
    
}

Test.s.length();

class System // System is a pre-define class in java

{

    static PrintStream out; // Here PrintStream is a class like String
    
}

System.out.println();

**what is public static void main(String args[])**

JVM is responsible for executing main method

**public:** means accessible everywhere

**static:** its a keyword which will be common accross all objects

**void:** its a return type

**main():** method name

**String args[]:** its an array

public static void main(String args[]) - valid and its an actual main method and jvm looks for actual main method to execute the programm

static public void main(String args[]) - in-valid

public void static main(String args[]) - in-valid

void main(String args[]) public static - invalid

public static void main(int a[]) - valid but its not an actual main method

**========================Inheritance=============================**

Acquiring all the variables and methods from one class to another class

**Advantage**

i) Re-usability

ii) Avoid duplication

**Inheritance Types**

**1) Single Inheritance**

**Note** one java file can have only one class as public, we can create object only in the main method and we can't create one method inside another method

class A 

{

    int a = 10;

    void display()

    {

        System.out.println(a);

    }

}

class B extends A

{

    int b = 10;

    void show()

    {

        System.out.println(b);

    }

}

public class Inheritance

{

    public static void main(String args[])

    {

        B bobj = new B();
        System.out.println(bobj.a);
        System.out.println(bobj.b);
        bobj.display();
        bobj.show();
    }

}

**2) Multi-level Inheritance**

class A 

{

    int a;

    void display()

    {

        System.out.println(a);

    }

}

class B extends A

{

    int b;

    void show()

    {

        System.out.println(b);

    }

}

class C extends B

{

    int c;

    void print()

    {

        System.out.println(c);

    }

}

public class Inheritance

{

    public static void main(String args[])

    {

        C cobj = new C();
        
        cobj.a=10;
        cobj.b=20;
        cobj.c=30;
        cobj.display();
        cobj.show();
        cobj.print();
    }

}

**Note:** In same package don't use same class name in same file as well as in different file becuase it will throw error

**3) hierarchical inheritance**

class Parent

{

    void display(int a)
    {
        System.out.println(a);
    }

}

class child1 extends Parent

{

    void show(int b)
    {
        System.out.println(b);
    }

}

class child2 extends Parent

{

    void print(int c)
    {
        System.out.println(c);
    }

}

public class HierarchicalInheritance

{

    public static void main(String args[])

    {

        child1 c1 = new child1();

        c1.display(10);
        
        c1.show(20);

        child2 c2 = new child2();

        c2.display(30);
        
        c2.print(40);
        
    }

}

**Note:** Multiple inheritance is not supported using class concept we can acheive it using interface in java

**Why multiple inheritance is not supported in class in java ?**

Reason1: extends keyword support only one class not two classes

Reason2: it creates ambiguity while extending when two class have same method...even though if we have two different methods still it creates ambiguity becuase whenever we create class it extends variables and methods from a root class also known as Object class. If we don't create any method inside class still class will have some methods which is extended from root class known as object class.

**============method overriding================**

1) having same method name in child class which is there in parent class but there will be change in implementation of child class method is known as method overriding

2) without inheritance overriding is not possible and method overriding is a concept of inheritance and overloading is a concept of polymorphism

3) there should be minimum one child class to override the method

example: 

class Bank

{

    double roi()

    {
        return 0;

    }

}

class ICICI extends Bank

{

    double roi()

    {
        return 10.0;

    }

}

class SBI extends Bank

{

    double roi()

    {
        return 11.0;

    }

}

class OverridingDemo

{

    public static void main(String args[])

    {

        ICICI i = new ICICI();
        
        System.out.println(i.roi());
    
        SBI s = new SBI();
        
        System.out.println(s.roi());

    }

}

4) we can achieve both overloading and overriding using inheritance

5) we can achieve overloading with or without inheritance

6) But overriding can be achieved only through inheritance

Example:

class ABC

{

    void m1(int a)
    
    {

        System.out.println(a);

    }

    void m2(int b)
    
    {

        System.out.println(b);

    }

}

class XYZ extends ABC

{

        void m1(int a) 
    
        {

            System.out.println(a*a); // Overriding

        }

        void m2(int a,int b)
    
        {

            System.out.println(a+b); // Overloading

        }

}

class OverloadingVsOverriding

{

    public static void main()

    {

        XYZ xyzObj = new XYZ();
        
        xyzObj.m1(10);
        
        xyzObj.m2(20);
        
        xyzObj.m2(10,20);

    }

}

7) if there are same methods in two different classes and there is no connection between them then we can't say that as overloadng 
         
Example:

class A

{

    int show(int a)
    
    {
    
        return a;
        
    }
    
}

class B

{

    int show(int a,int b)
    
    {
    
        return a+b;
        
    }
    
}

class Main 
{

    public static void main(String[] args)
    {
    
        A a = new A();
        
        System.out.println(a.show(10));
        
        B b = new B();
        
        System.out.println(b.show(20,30));
        
    }
    
}

**============final keyword=======================**

final keyword can be applied to class, variables and methods

**example 1:** For variable

class Test

{

    final int x = 100;

}

public class FinalKeyword

{

    public static void main(String args[])

    {

        Test t = new Test();
        
        t.x = 200; //In-correct because we can't change value of final variable it is constant
        
        System.out.println(t.x);

    }

}

**example 2:** For method

class Test1

{

    final void m()

    {

        System.out.println("This is method from Test1...");

    }

}

class Test2 extends Test1

{

    void m() //In-correct, we can't override this method because it's final

    {

        System.out.println("This is method from Test2...");

    }

}

public class FinalKeyword

{

    public static void main(String args[])

    {

        Test2 t2 = new Test2();
        
        t2.m();

    }

}

**example 3:** For class

final class Test1

{

    void m()

    {

        System.out.println("This is method from Test1...");

    }

}

class Test2 extends Test1 //In-correct, we can't extend Test1 class because it's final

{

    void m() 

    {

        System.out.println("This is method from Test2...");

    }

}

public class FinalKeyword

{

    public static void main(String args[])

    {

        Test2 t2 = new Test2();
        
        t2.m();

    }

}

**=============super keyword=================**

1) Here we will be creating an object of child class and if we want to accessing method or variables of parent class then we need to use super keyword

2) super keyword will be used to invoke the immediate parent class variable

3) super keyword will be used to invoke the immediate parent class method

4) super keyword is not applicable for multiple inheritance

5) super keyword doesn't support interface it supports only for class

**Example:** super keyword for variable

class Animal

{

    String color = "white";

}

class Dog extends Animal

{

    String color = "black";

    void DisplayColor()

    {

        System.out.println(super.color);

    }

}

class SuperKeyword

{

    public static void main(String args[])
    
    {
    
        Dog d = new Dog();
    
        d.DisplayColor();
    
    }

}

**Example:** super keyword for method

class Animal

{

    void eat()

    {

        System.out.println("eating...");

    }

}

class Dog extends Animal

{

    void eat()

    {

        super.eat();

    }

}

class SuperKeyword

{

    public static void main(String args[])
    
    {
    
        Dog d = new Dog();
    
        d.eat();
    
    }

}
        
**===========Data Abstraction=================**   

Data abstraction is a process of hiding implementation details and showing only functionality to the user

1) Abstract class

2) Interface

**Interface:**

-> An interface is a blue print of a class

    Example :

            class Test            **||**        Interface Test

            {                     **||**        {

                variables         **||**            variables

                methods           **||**            methods

            }                     **||**        }

-> Variables are final ans static by default in interface

-> Interface contains abstract methods (Also allowed default and static methods from java8 onwards)

-> Abstract method contains only signature but not body or implementation

Example :

            class Test                **||**        Interface Test

            {                         **||**        {

                void main()           **||**            void main(); // abstract method
                
                {                     **||**        }
                
                    implementation    **||**            

                }                     **||**            

            }                         **||**      

-> Methods in interface are public where as in class it is default and no need to write default keyword and if you write also not a problem

-> Interface supports multiple inheritance

-> We define interface with inerface keyword

Example :

            class Test            **||**        Interface Test

            {                     **||**        {

                variables         **||**            variables

                methods           **||**            methods

            }                     **||**        }

-> A class extends another class, An interface extends another interface but class implements interface for the purpose of abstract menthods

-> In interface we can't create object but we can create reference variable(means we can create object of class and hold that object into reference variable of type class or into reference variable of type interface)

**Why we create abstract methods because it doesn't have any implementation inside it and what is the use of creating it then?**

We create it because initially developer won't be knowing how to develop they will just know what to develop so they will just create abstract methods without any implementation once they get to know how to develop then they start implementing using class...this is the reason we create abstract method in interface without implementation inside it.



