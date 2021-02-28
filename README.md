# JavaGenericsRTF2 | Mohamed Sofiene Barka | RT2.2

## Intro
+ Writing a Linked Lists class? what would it hold? Integers, Chars, Strings...?
+ Unless you write a Class for each type in Java and hope that programmer doesn't need a custom Linked List for his own made up class, you're Okay!
or just use Generics..
+ Generics are a Way to Work with IDK-TYPES and use them as Aliases to whatever type the programmer will use
+ It were added to Java 5.0 in 2004

## How
+ when creating : Define an Alea to whatever Type, and use it as THAT TYPE xD
+ when use : You will Let the constructor know about the Types used else it won't make any sense LOL
+ <TypeName> : you'll use such way, you can use mutiple Aleases : for a Map for example : <KeyType, ValType>
```java
class ClassName <TypeAlea> {
  public ClassName(TypeAlea ParamOfThatType){}
} 
// somewhere else..
ClassName<TypeRef like Integer, String, any Object> x = new ClassName<TypeRef>(params);

```

## Code would make Sense..

+ Lets make a Number Class, it can take any kind of numbers (Integers, Real Numbers, Complexe -Let's Suppose we've done one-..)

> This Won't work because it expects an Integer, how would I make a Number out of 4.2
```java
class Number {
  private int x;
  public Number(int x) {
    this.x = x;
  }
  public int get() {return x;}
}

class Main {
  public static void main(String[] args) {
    Number x = new Number(4.2);
    System.out.println(x.get());
  }
}
```

> Sike
```java
class Number <T> {
  private T x;
  public Number(T x) {
    this.x = x;
  }
  public T get() {return x;}
}

class Main {
  public static void main(String[] args) {
    Number<Float> x = new Number<Float>(4.2f);
    System.out.println(x.get());
  }
}
```

> even with custom classes, didn't change anything with the Number Class..
```java
class Complex {
  private int x, y;
  public Complex(int x, int y) {
    this.x = x;
    this.y = y;
  }
  public String toString() {
    return x + ( y > 0 ? "+" : "-") + "j" + Math.abs(y); 
  }
}

class Number <T> {
  private T x;
  public Number(T x) {
    this.x = x;
  }
  public T get() {return x;}
}

class Main {
  public static void main(String[] args) {
    Number<Complex> x = new Number<Complex>( new Complex(1, -7));
    System.out.println(x.get());
  }
}
```

**Generic type should be Reference as It looks, you can't use int, use Integer, same for Float and Double**
**Strings and Objects are references already, so no problem with them..**
**That's why C++ is Better!**

**Complex can contain whatever Numbers too.. but implementing that was painful.. nvm**

## More Coding.. Key-Value Pair ig!? Let's make a Small Redis Clone..
> No Refernce when Defining, Allowing All Types!
```java
// K for Keys, V for Values..
class Redis <K, V> {
  private K key;
  private V value;
  public Redis(K key, V value) {
    this.key = key;
    this.value = value;
  }
  public void set(V value) {
    this.value = value;
  }
  public V get(K key) {
    if (this.key == key) return value;
    throw new Error("Undefined");
  }
  public String toString() {
    return key + ": " + value + "\n"; 
  }
}

class Main {
  
  public static void main(String[] args) {
    Redis x = new Redis("id", 15665);
    // didn't know you can do that xD
    x.set("bruh");

    System.out.println(x);
  }
}
```
> Now you should use whatevr you specified when Creating the Object
```java
class Redis <K, V> {
  private K key;
  private V value;
  public Redis(K key, V value) {
    this.key = key;
    this.value = value;
  }
  public void set(V value) {
    this.value = value;
  }
  public V get(K key) {
    if (this.key == key) return value;
    throw new Error("Undefined");
  }
  public String toString() {
    return key + ": " + value + "\n"; 
  }
}

class Main {
  
  public static void main(String[] args) {
    Redis <String, Integer> x = new Redis <String, Integer>("id", 15665);
    // It doesnt Work now
    // x.set("bruh");

    x.set(11447);
    System.out.println(x);
  }
}
```
