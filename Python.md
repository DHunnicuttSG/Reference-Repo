# OOP Python
Below is a simple an example in Python. Anyone coming into the training with a Java background will appreciate!


```py
class Animal:
    """
    This is a demo class
    """
    def __init__(self, name="", age=0, weight=0):
        """
        Initializes an instance of Animal with the given name, age, and weight.

        This method is invoked automatically when a new instance of Animal is created.
        """
        self.name = name
        self.age = age
        self.weight = weight

    def __repr__(self):
        """
        Returns a string representation of the Animal object.

        This method is invoked automatically when the object needs to be represented as a string,
        such as when printed or when used in string formatting.
        """
        return f"{self.__class__.__name__}(Name: {self.name}, Age: {self.age}, Weight: {self.weight})"

    def __eq__(self, other):
        """
        Compares the Animal object with another object for equality.

        This method is invoked automatically when the '==' operator is used to compare two Animal objects.
        """
        return (
            self.name == other.name and
            self.age == other.age and
            self.weight == other.weight
        )

    def eat(self):
        """
        Simulates the eating behavior of the Animal.
        """
        print(f"{self.__class__.__name__} is eating")

    @staticmethod
    def is_animal(obj):
        """
        Checks if the given object is an instance of Animal or its subclass.

        Parameters:
            obj: object to be checked
        Returns:
            bool: True if the object is an instance of Animal or its subclass, False otherwise.
        """
        return isinstance(obj, Animal)


class Feline:
    def __init__(self, lives=9):
        """
        Initializes an instance of Feline with the given number of lives.

        This method is invoked automatically when a new instance of Feline is created.
        """
        self._lives = lives

    @property
    def lives(self):
        """
        Retrieves the number of lives of the Feline.

        Returns:
            int: The number of lives of the Feline.
        """
        return self._lives

    @lives.setter
    def lives(self, value):
        """
        Sets the number of lives of the Feline.

        Parameters:
            value (int): The number of lives to set.
        """
        if value is not None and not (1 <= value <= 9):
            raise ValueError("Lives must be in the range 1 to 9")
        self._lives = value
    def eat(self):
        """
        Simulates the eating behavior of the Cat.
        """
        print(f"{self.__class__.__name__} is eating... purrrr")


class Cat(Animal, Feline):
    """
    Cat extends the Animal class and includes Feline traits
    """
    def __init__(self, name="", age=0, weight=0, lives=9):
        """
        Initializes an instance of Cat with the given name, age, weight, and number of lives.

        This method is invoked automatically when a new instance of Cat is created.
        """
        Animal.__init__(self, name, age, weight)
        Feline.__init__(self, lives)
    def eat(self):
        Feline.eat(self)
    def __eq__(self, other):
        return(
            self.lives == other.lives
            and Animal.__eq__(self, other)
        )



def feed_animals(animal):
    """
    Checks if the provided object is an instance of Animal and calls its eat method.

    Parameters:
        animal: object to perform eating behavior
    """
    if Animal.is_animal(animal):
        animal.eat()
    else:
        print("Object is not an instance of Animal or its subclass")


a1 = Cat(name="George", age=3, weight=5, lives=7)
a2 = Cat(name="George", age=3, weight=5, lives=7)
a3= Cat()

print(a3)


print(a1)
print(a1 == a2)

feed_animals(a1)

# Call the static method
print(Animal.is_animal(a1))  # Should print True
print(Animal.is_animal("Not an animal"))  # Should print False

# Test getter and setter for lives
print(a1.lives)  # Should print 7
a1.lives = 5
print(a1.lives)  # Should print 5

# Demonstrate rejecting an update
try:
    a1.lives = 10  # This should raise a ValueError
except ValueError as e:
    print(e)  # Should print "Lives must be in the range 1 to 9"

# Compare objects after updating lives
print(a1 == a2)  # Should print False

```

# Generators
Generators are core components in Python. Below is an example of a generator for generating primes.

```py
def generate_primes(n):
    primes = []
    num = 2
    while len(primes) < n:
        is_prime = True
        for prime in primes:
            if num % prime == 0:
                is_prime = False
                break
        if is_prime:
            primes.append(num)
            yield num
        num += 1

# Example usage:
n = 10
prime_generator = generate_primes(n)
print(f"The first {n} prime numbers are:")
for prime in prime_generator:
    print(prime)

import sys

a = range(1000) # generators yield one value into memory at a time
b = [i for i in range(1000)] # a list has all its data in memory

# compare the sizes
print(f"Size of a generator {sys.getsizeof(a)}")
print(f"Size of similar list {sys.getsizeof(b)}")

```
