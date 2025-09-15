# The four pillars of Object-Oriented Programming (OOP) explained using an anology of a drive-thru fast-food restaurant.

## 🔒 Encapsulation: The Car and the Order Box
Encapsulation is about bundling data (attributes) and methods (behaviors) together within a single unit and hiding the internal details from the outside world. Think of your car in the drive-thru line. The driver's cabin is the public interface, with a steering wheel and pedals. The intricate workings of the engine, transmission, and fuel injectors are hidden away under the hood. You don't need to understand how the engine works to drive the car; you just interact with the simple interface. Similarly, the drive-thru order box is an encapsulated object. You just talk into the speaker, and it handles all the complex logic of converting your voice into an order for the kitchen, without revealing how it works.

## 🧬 Inheritance: The Menu Items
Inheritance is when a new class, or "child class," derives properties and behaviors from an existing "parent class." This allows you to create a hierarchy of related objects. In our restaurant, all the food items could inherit from a base class like MenuItem. A Burger and a Salad are both MenuItems, so they share common properties like Name, Price, and Description. However, each item can add its own unique properties. The Burger class might have a numberOfPatties property, while the Salad class has a dressingType property. This lets you reuse common code while still creating distinct, specialized items.

## 🎭 Polymorphism: The "Make" Command
Polymorphism means "many forms." It allows objects to be treated as a common type while still retaining their unique behaviors. Imagine a new order coming into the kitchen. The kitchen staff receives a generic command: "Make the order."  However, the specific action they perform depends on the item. If the order is for a Burger, they grill a patty. If it's for Fries, they drop potatoes into the fryer. If it's for a Milkshake, they blend ice cream. The same command ("Make the order") produces different, specialized results based on the object it's acting on.

## 🧊 Abstraction: The Menu Board
Abstraction is the process of hiding complex implementation details and showing only the necessary features of an object. The drive-thru menu board is a perfect example of abstraction. It shows you appealing pictures and names of meals (e.g., "The Classic Combo") without a single detail about how the food is sourced, prepared, or cooked. The menu abstracts away the complexity of the kitchen and presents a simple, high-level interface that allows you to make a choice. You only interact with the essential information you need to place your order.


## Composition Examples:

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
