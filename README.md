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

class Test
{
    static String s = "welcome"; // here String is a class
}

Test.s.length();

class System
{
    static PrintStream out; // Here PrintStream is a class like String
}

System.out.println();
