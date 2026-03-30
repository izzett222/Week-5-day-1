# Mental Model Questions

## **1. Static Initialization Blocks**
1. When exactly are static initialization blocks executed in the lifecycle of a Java class?
2. What is the order of execution if a class has multiple static variables and multiple static blocks?
3. Can static initialization blocks access instance variables or instance methods? Why or why not?
4. Imagine you have multiple static values that depend on each other. Why would a static block be preferred over inline initialization?
5. Do static blocks run every time an object is created? Explain.

## 2. Instance Initialization Blocks
1. When are instance initialization blocks executed relative to constructors and superclass constructors?
2. Can instance initialization blocks access static members? Can they access instance members that haven’t been initialized yet?
3. If a class has multiple instance initialization blocks, in what order are they executed?
4. How does an instance initialization block differ from a constructor in terms of flexibility and reuse?
5. Why might you choose an instance block over duplicating code in multiple constructors?
# Exercises

## Exercise 1: Static Block Execution
```java
class DemoStatic {  
    static int x = 5;  
  
    static {  
        x = x * 2;  
        System.out.println("Static block 1: x = " + x);  
    }  
  
    static {  
        x = x + 3;  
        System.out.println("Static block 2: x = " + x);  
    }  
  
    public static void main(String[] args) {  
        System.out.println("Main method: x = " + x);  
    }  
}

```

**Tasks:**
1. Predict the output of this program.
2. Explain the order in which the static blocks and static variables are initialized.
3. What happens if `DemoStatic` is never referenced in `main`?

---

### **Exercise 2: Instance Initialization Block**
```java
class DemoInstance {  
    String name;  
  
    {  
        name = "default";  
        System.out.println("Instance block 1: name = " + name);  
    }  
  
    {  
        name = "updated";  
        System.out.println("Instance block 2: name = " + name);  
    }  
  
    DemoInstance(String name) {  
        this.name = name;  
        System.out.println("Constructor: name = " + this.name);  
    }  
  
    public static void main(String[] args) {  
        DemoInstance obj = new DemoInstance("custom");  
    }  
}

```

**Tasks:**
1. Predict the output when creating a new `DemoInstance`.
2. Explain why the instance blocks execute before the constructor.
3. If the class had a superclass with its own constructor, where would the superclass constructor run relative to these instance blocks?
### **Exercise 3: Combining Static and Instance Blocks**
```java
class Combo {  
    static int count;  
    String id;  
  
    static {  
        count = 100;  
        System.out.println("Static block: count = " + count);  
    }  
  
    {  
        id = "user" + count;  
        System.out.println("Instance block: id = " + id);  
    }  
  
    Combo() {  
        System.out.println("Constructor: id = " + id);  
    }  
  
    public static void main(String[] args) {  
        Combo c1 = new Combo();  
        Combo c2 = new Combo();  
    }  
}
```


**Tasks:**
1. Predict the output.
2. Explain how many times each block runs and why.
3. What would change if `count` were not static?
