# Mindset
A student once asked Bruce Lee, “You teach me fighting, but you talk about peace. How do you reconcile the two?”
Bruce Lee beautifully replied, “It’s better to be a warrior in a garden than to be a gardener in a war.”

# One-line GraalVM JDK Downloads
``` 
bash <(curl -sL https://get.graalvm.org/jdk)
```
## Specific GraalVM release
```
bash <(curl -sL https://get.graalvm.org/jdk) graalvm-ce-java11-22.3.0
```
## For all options
```
bash <(curl -sL https://get.graalvm.org/jdk) --help
```
## download the script and inspect it before running
```
# download the GraalVM JDK Downloader script
curl -OL https://get.graalvm.org/jdk
# inspect the script
less jdk
# run the script
bash jdk
```

# Feign Client
* Exception Handling with ErrorDecoder
* Exception Handling with Fallback
* Exception Handling with FallbackFactory

# Java 14 - Switch Expressions
* Old 
```
public enum Day { SUNDAY, MONDAY, TUESDAY,
    WEDNESDAY, THURSDAY, FRIDAY, SATURDAY; }

// ...

    int numLetters = 0;
    Day day = Day.WEDNESDAY;
    switch (day) {
        case MONDAY:
        case FRIDAY:
        case SUNDAY:
            numLetters = 6;
            break;
        case TUESDAY:
            numLetters = 7;
            break;
        case THURSDAY:
        case SATURDAY:
            numLetters = 8;
            break;
        case WEDNESDAY:
            numLetters = 9;
            break;
        default:
            throw new IllegalStateException("Invalid day: " + day);
    }
    System.out.println(numLetters);
```
* New
```
    Day day = Day.WEDNESDAY;    
    System.out.println(
        switch (day) {
            case MONDAY, FRIDAY, SUNDAY -> 6;
            case TUESDAY                -> 7;
            case THURSDAY, SATURDAY     -> 8;
            case WEDNESDAY              -> 9;
            default -> throw new IllegalStateException("Invalid day: " + day);
        }
    );    
```
# Java 15 - Text Blocks
* Original
```
String message = "'The time has come,' the Walrus said,\n" +
                 "'To talk of many things:\n" +
                 "Of shoes -- and ships -- and sealing-wax --\n" +
                 "Of cabbages -- and kings --\n" +
                 "And why the sea is boiling hot --\n" +
                 "And whether pigs have wings.'\n";
```
* Better
```
String message = """
    'The time has come,' the Walrus said,
    'To talk of many things:
    Of shoes -- and ships -- and sealing-wax --
    Of cabbages -- and kings --
    And why the sea is boiling hot --
    And whether pigs have wings.'
    """;
```
# Java 16 - Record classes
* In many cases, this data is immutable, since immutability ensures the validity of the data without synchronization.
* Old style
```
public class Person {

    private final String name;
    private final String address;

    public Person(String name, String address) {
        this.name = name;
        this.address = address;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, address);
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) {
            return true;
        } else if (!(obj instanceof Person)) {
            return false;
        } else {
            Person other = (Person) obj;
            return Objects.equals(name, other.name)
              && Objects.equals(address, other.address);
        }
    }

    @Override
    public String toString() {
        return "Person [name=" + name + ", address=" + address + "]";
    }

    // standard getters
}
```
* Replacement 
```
public record Person (String name, String address) {}
```
# Java 16 - Pattern Matching for instanceof
* Old style
```
public interface Shape {
    public static double getPerimeter(Shape shape) throws IllegalArgumentException {
        if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return 2 * r.length() + 2 * r.width();
        } else if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            return 2 * c.radius() * Math.PI;
        } else {
            throw new IllegalArgumentException("Unrecognized shape");
        }
    }
}

public class Rectangle implements Shape {
    final double length;
    final double width;    
    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }    
    double length() { return length; }
    double width() { return width; }
}

public class Circle implements Shape {
    final double radius;
    public Circle(double radius) {
        this.radius = radius;
    }  
    double radius() { return radius; }
}
```
* Replacement 
```
public static double getPerimeter(Shape shape) throws IllegalArgumentException {
   if (shape instanceof Rectangle r) {
      return 2 * r.length() + 2 * r.width();
   } else if (shape instanceof Circle c) {
      return 2 * c.radius() * Math.PI;
   } else {
      throw new IllegalArgumentException("Unrecognized shape");
   }
}
```
