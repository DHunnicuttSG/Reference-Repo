# Composition Examples:

In Object-Oriented Programming, composition means building complex objects by combining simpler ones, rather than relying only on inheritance.
Think of a DriveThruRestaurant object:  
A drive-thru restaurant is composed of several parts, each of which is its own class:

Menu (represents food options)  
OrderSystem (takes and manages orders)  
PaymentProcessor (handles payments)  
Kitchen (prepares the food)  
DriveThruLane (manages cars in line)  

Instead of making DriveThruRestaurant inherit from Kitchen or Menu (which wouldn’t make sense), we say:
👉 A DriveThruRestaurant has a Kitchen, Menu, OrderSystem, etc.

Code Analogy in Java
```java
class Menu {
    void showItems() {
        System.out.println("Burgers, Fries, Shakes...");
    }
}

class OrderSystem {
    void takeOrder() {
        System.out.println("Taking order...");
    }
}

class PaymentProcessor {
    void processPayment() {
        System.out.println("Processing payment...");
    }
}

class Kitchen {
    void prepareFood() {
        System.out.println("Cooking food...");
    }
}

class DriveThruRestaurant {
    private Menu menu;
    private OrderSystem orderSystem;
    private PaymentProcessor paymentProcessor;
    private Kitchen kitchen;

    // Composition: DriveThruRestaurant is made of these parts
    public DriveThruRestaurant() {
        this.menu = new Menu();
        this.orderSystem = new OrderSystem();
        this.paymentProcessor = new PaymentProcessor();
        this.kitchen = new Kitchen();
    }

    public void serveCustomer() {
        menu.showItems();
        orderSystem.takeOrder();
        paymentProcessor.processPayment();
        kitchen.prepareFood();
        System.out.println("Order ready! Handing food through the window.");
    }
}

public class Main {
    public static void main(String[] args) {
        DriveThruRestaurant restaurant = new DriveThruRestaurant();
        restaurant.serveCustomer();
    }
}
```

* Key Takeaway

Inheritance = "is-a" (e.g., Cheeseburger is a MenuItem).  
Composition = "has-a" (e.g., DriveThruRestaurant has a Menu, has a Kitchen).


## Another Composition Example:

Let’s extend the analogy with cars in the drive-thru line — this will show how composition makes bigger systems out of smaller ones.

🚗 Extended Analogy: Cars in the Drive-Thru

In the real world, a drive-thru restaurant doesn’t exist in isolation — it serves customers in cars.  
Each Car might have a Driver and some Passengers.  
A DriveThruLane manages all the cars waiting in line.  
The DriveThruRestaurant is composed of a DriveThruLane in addition to its Menu, Kitchen, etc.

So:

* A Car has-a Driver.

* A DriveThruLane has Cars.

* A DriveThruRestaurant has a DriveThruLane (and everything else).

💻 Example in Java
```java
import java.util.LinkedList;
import java.util.Queue;

class Driver {
    private String name;

    public Driver(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

class Car {
    private Driver driver;

    public Car(Driver driver) {
        this.driver = driver;
    }

    public Driver getDriver() {
        return driver;
    }
}

class DriveThruLane {
    private Queue<Car> cars = new LinkedList<>();

    public void addCar(Car car) {
        cars.add(car);
    }

    public Car nextCar() {
        return cars.poll();
    }

    public boolean hasCars() {
        return !cars.isEmpty();
    }
}

class Menu {
    void showItems() {
        System.out.println("Menu: Burgers, Fries, Shakes...");
    }
}

class OrderSystem {
    void takeOrder(Driver driver) {
        System.out.println(driver.getName() + " places an order.");
    }
}

class PaymentProcessor {
    void processPayment(Driver driver) {
        System.out.println(driver.getName() + " pays for the order.");
    }
}

class Kitchen {
    void prepareFood() {
        System.out.println("Kitchen: Cooking food...");
    }
}

class DriveThruRestaurant {
    private Menu menu = new Menu();
    private OrderSystem orderSystem = new OrderSystem();
    private PaymentProcessor paymentProcessor = new PaymentProcessor();
    private Kitchen kitchen = new Kitchen();
    private DriveThruLane lane = new DriveThruLane();

    public void addCarToLine(Car car) {
        lane.addCar(car);
    }

    public void serveCustomers() {
        while (lane.hasCars()) {
            Car car = lane.nextCar();
            Driver driver = car.getDriver();

            System.out.println("\nNow serving: " + driver.getName());
            menu.showItems();
            orderSystem.takeOrder(driver);
            paymentProcessor.processPayment(driver);
            kitchen.prepareFood();
            System.out.println("Order ready for " + driver.getName() + "!\n");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        DriveThruRestaurant restaurant = new DriveThruRestaurant();

        restaurant.addCarToLine(new Car(new Driver("Alice")));
        restaurant.addCarToLine(new Car(new Driver("Bob")));
        restaurant.addCarToLine(new Car(new Driver("Charlie")));

        restaurant.serveCustomers();
    }
}
```
📝 Sample Output
```java
Now serving: Alice
Menu: Burgers, Fries, Shakes...
Alice places an order.
Alice pays for the order.
Kitchen: Cooking food...
Order ready for Alice!

Now serving: Bob
Menu: Burgers, Fries, Shakes...
Bob places an order.
Bob pays for the order.
Kitchen: Cooking food...
Order ready for Bob!

Now serving: Charlie
Menu: Burgers, Fries, Shakes...
Charlie places an order.
Charlie pays for the order.
Kitchen: Cooking food...
Order ready for Charlie!
```

✅ This shows composition in action:

* A Car has a Driver.
* A DriveThruLane has Cars.
* A DriveThruRestaurant has a DriveThruLane, Menu, OrderSystem, PaymentProcessor, and Kitchen.