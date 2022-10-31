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
