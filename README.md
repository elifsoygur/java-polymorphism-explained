# java-polymorphism-explained

Let's examine the topic of polymorphism through 4 different examples.
I will go from simple to tricky.
The first example is a classic one:
Let's have an Animal class, a Bird class that extends it, and a BabyBird class that extends Bird.
Something like this:
class Animal {
   void sleep() {
        System.out.println("Animals sleep");
    }  
}
class Bird extends Animal {
   @override
    void sleep() {
        System.out.println("Birds sleep");
    }
    void fly() {
        System.out.println("Birds fly");
    }
}
class BabyBird extends Bird {
      void sing() {
        System.out.println("Babybirds sing");
    }
      @override
      void fly() {
        System.out.println("BabyBirds fly");
    }
}
public class Main {
    public static void main(String[] args) {
        Bird b = new BabyBird();  
        b.sleep();  
    }
}
        
Let's start by discussing the first example.

Rule 1: If the reference class does not contain the relevant method, you will get a compiler error even if the method is defined in the object’s class.

Example:
class Animal {
   void sleep() {
        System.out.println("Animals sleep");
    }  
}
class Bird extends Animal {
   @override
    void sleep() {
        System.out.println("Birds sleep");
    }
}
class BabyBird extends Bird {
      void sing() {
        System.out.println("Babybirds sing");
    }
      @override
       void fly() {
        System.out.println("BabyBirds fly");
    }
}
public class Main {
    public static void main(String[] args) {
        Bird b = new BabyBird();  
        b.fly();    //Since the fly method is not defined in the Bird class and not overridden in its subclass, we get an error even though the method exists in 
                      the object's actual class.
    }
}
 
Rule 2: If the method is not defined in the reference class of the object, it might be defined in one of its superclasses.
Example:
class Animal {
   void sleep() {
        System.out.println("Animals sleep");
    } 
    void sing() {
        System.out.println("Animals sing");
    }
}
class Bird extends Animal {
   @override
    void sleep() {
        System.out.println("Birds sleep");
    }
}
class BabyBird extends Bird {
      
}
public class Main {
    public static void main(String[] args) {
        Bird b = new BabyBird();  
        b.sing();    //Animals sing
    }
}

Rule 3: You have to take the ladder one step at a time.
Example:
class Animal {
   void sleep() {
        System.out.println("Animals sleep");
    
     }  
     void sing() {
        System.out.println("Animals sing");
    }
}
class Bird extends Animal {
    void sing() {
        System.out.println("Birds sing");
    }
    void fly() {
        System.out.println("Birds fly");
    }
}
class BabyBird extends Bird {
    
    void fly() {
        System.out.println("BabyBirds fly");
    }
}
public class Main {
    public static void main(String[] args) {
        Animal a = new Babybird();  //Here, I want the animal to behave like a Babybird. 
        a.sing();    //   First, check whether referance class includes the method. If yes, then start to climb the ladder one step at each time on the right handside.  So, Birds sing.     
    }
Rule 4: It is sufficient for the method to be in the reference class; there is no need to look for it in the superclasses of the reference.

Example
class Animal {
  
}
class Bird extends Animal {
    void sing() {
        System.out.println("Birds sing");
    }
    void fly() {
        System.out.println("Birds fly");
    }
}
class BabyBird extends Bird {
    
    void fly() {
        System.out.println("BabyBirds fly");
    }
}
public class Main {
    public static void main(String[] args) {
       Bird b= new Babybird();  
       b.fly() //BabyBirds fly

