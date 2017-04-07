## Example Language Specific Problem

### Problem name
Java onboarding task

### Description
When working in teams, a software developer is required to write code based on requirements specified by the lead architect or other members in the team. This helps to speed up the software development process as the developers can avoid the conflicts during the integration.

Being your first day in the team, your lead architect wanted to test your basics in Java. Your first task is to implement a Java code based on the following specification. Note that your code should exactly match the specification. Consider default visibility of classes, data fields, and methods unless mentioned otherwise.

Class: Vehicle

* Method: speedUp
  * Description: add the increment to the speed of the vehicle
  * Parameters: int
  * Returns: void
  * Method signature: void speedUp(int increment)
  * visibility: public
* Method: applyBrakes
  * Description: subtract the decrement from the speed of the vehicle
  * Parameters: int
  * Returns: void
  * Method signature: void applyBrakes(int decrement)
  * visibility: public
* Method: getSpeed
  * Parameters: void
  * Returns: int
  * Method signature: int getSpeed()
  * visibility: public

Note that the speed of the vehicle can never be zero.

### Example
```java
Vehicle vehicle = new Vehicle();

assert(vehicle.getSpeed() == 0); // Initial speed should be zero

vehicle.speedUp(5);
assert(vehicle.getSpeed() == 5); // Current speed should be 5 after speeding up

vehicle.applyBrakes(3);
assert(vehicle.getSpeed() == 2); // Current speed should be 2 after applying brakes
```

### Solution
```java
import java.lang.Math;

class Vehicle {
    private int speed = 0;

    public void speedUp(int increment) {
        this.speed += increment;
    }

    public void applyBrakes(int decrement) {
        this.speed = Math.min(this.speed - decrement, 0);
    }

    public int getSpeed() {
        return this.speed;
    }
}
```

### Testcases
Note that the classes defined by the user will be in the classpath so the evaluation script does not need to import it. And the classes defined by the user should always use default access specifier.

### Sample testcase
Check if all the methods exists. Do not check the implementation of the methods in sample testcase.

```java
// class name should be eval
class eval {

    public static void main(String[] args) {

        Vehicle vehicle = new Vehicle();
        int currentSpeed;

        currentSpeed = vehicle.getSpeed();
        vehicle.speedUp(1);
        vehicle.applyBrakes(1);
    }
}
```

### Testcases

#### Check implementation of speedUp
```java
// class name should be eval
class eval {

    public static void main(String[] args) {

        Vehicle vehicle = new Vehicle();

        assert(vehicle.getSpeed() == 0); // Initial speed should be zero

        vehicle.speedUp(5);
        assert(vehicle.getSpeed() == 5); // Current speed should be 5 after speeding up
    }
}
```

#### Check implementation of applyBrakes
```java
// class name should be eval
class eval {

    public static void main(String[] args) {

        Vehicle vehicle = new Vehicle();

        assert(vehicle.getSpeed() == 0); // Initial speed should be zero

        vehicle.applyBrakes(3);
        assert(vehicle.getSpeed() == 0); // Current speed should be zero after applying brakes
    }
}
```

#### Check the complete class
```java
// class name should be eval
class eval {

    public static void main(String[] args) {

        Vehicle vehicle = new Vehicle();

        assert(vehicle.getSpeed() == 0); // Initial speed should be zero

        vehicle.speedUp(5);
        assert(vehicle.getSpeed() == 5); // Current speed should be 5 after speeding up

        vehicle.applyBrakes(9);
        assert(vehicle.getSpeed() == 0); // Current speed should be zero after applying brakes
    }
}
```