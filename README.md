# CORE-JAVA-FOUNDATOION

**STATIC KEYWORD**
**1. Static methods can access static stuff directly (without object).**
   EXAMPLE: public class StaticAccessStatic {
    
    static int a = 10;

    static void m1() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {
        staticMethod(); 
        System.out.println(a);
    }
}

**2. Static methods can access non-static stuff through object.**
public class StaticAccessNonStatic {
    
    int a=10;

    void staticMethod() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {
        StaticAccessNonStatic s = new StaticAccessNonStatic();
        s.staticMethod();
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
        m1();
        m2();
    }

    static void m1()
    {
        System.out.println("This is m1 method");
    }

    void m2()
    {
        System.out.println("This is m2 method");
    }

    public static void main(String[] args) {
        NonStaticAccessAll obj = new NonStaticAccessAll();
        obj.m1();
    }
}
