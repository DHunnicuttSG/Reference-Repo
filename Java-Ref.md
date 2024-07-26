## Java Naming Conventions:
- Constants are named in all caps.  Example: final float TAX_RATE = .065;
- Variable names are camel case: the first letter of the second word is capitalized as well as any following words. Example:  thisVariable, myFirstName

## NetBeans/IntelliJ Shortcuts:
```Crtl + Shift + I``` = import libraries

```sout + Tab``` = System.out.println()

```psvm + Tab``` = public static void main(String[] args) {} 

## Java Data Types:
| Type | Contains | Default | Size | Range |
|------|----------|---------|------|-------|
|boolean | true or false | false | 1 bit | NA |
|Char | Unicode character | \u0000 | 16 bits | \u0000 to \uFFFF|
|Byte | Signed integer | 0 | 8 bits | -128 to 127|
|short | Signed integer | 0 | 16 bits | -32768 to 32767|
|int | Signed integer | 0 | 32 bits | -2147483648 to 2147483647|
|long | Signed integer | 0 | 64 bits | -9223372036854775808 to 9223372036854775807|
|float | IEEE 754 floating point | 0.0 | 32 bits | ±1.4E-45 to ±3.4028235E+38|
|double | IEEE 754 floating point | 0.0 | 64 bits | ±4.9E-324 to ±1.7976931348623157E+308|

## Java Code Syntax
Main method code example:
```
public static void main(String[] args) {
    System.out.println(“Text typed here displays on the console”);
}    
```

If Statement:
```
if (condition) { 
   // execute code if condition is true
}
```

If-Else Statement:
```
if (condition) {
    // execute code if condition is true
} else {
    // execute code if condition is false
}
```

Switch Statement:
```
switch (expression) {
    case constant:
        // execute code if expression == constant
        break;
    case constant2:
        //execute code if expression == constant2
        break;
    default:
        //execute code if no match found
        break;
}
```

Do Loop:
```
do {
    // code I want to repeat while condition is true
    // *** This loop is ALWAYS run At Least once ***
} while (condition);
```

While Loop:
```
while (condition) {
    // code I want to repeat while condition is true
    // add increment code to be sure you eventually meet condition
}
```

For Loop:
```
For (int i = 0; i < quizScore.length; i++) {
    System.out.println(“Quiz Score: ” + quizScore[i]);
}
```

Random numbers:
```
    //This code generates a random number between 1 and 10 inclusive
    Random rGen = new Random();   
    int rInt = rGen.nextInt(10) + 1;
```

Method Signature = method name and parameter list (could also include thrown exceptions)
Method Example:
```
    public static addNumbers(int operand1, int operand2) {
        return operand1 + operand2;
    }
```
Scanner code example:
```
    // declare and initial the Scanner
    Scanner myScanner = new Scanner(System.in);
    // get input from the user
    System.out.println("Please enter window height:");
    stringHeight = myScanner.nextLine();
```
## Java Operators
```A = 5``` means the variable A now has the value of 5
```A == 5``` means that you are testing if A equals 5.  This statement evaluates to true or false. A does NOT change value.

The symbols ```||``` mean OR  

The symbols ```&&``` mean AND

The symbol ```!``` In front of another symbol means NOT.  != means not equal to

## Java Data Structures
Arrays:
```
    //Arrays start with index ZERO
    //Initialize an Array:
    int[] quizScores = new int[4];
    quizScores[0] = 88;
    quizScores[1] = 92;
    quizScores[2] = 78;
    quizScores[3] = 96;
    
    //OR...
    
    int[] quizScores = {88, 92, 78, 96};

```

HashMaps:
```
    //Create Hashmap with String key and Int value
    Map<String, Integer> pops = new HashMap<>();
        pops.put("USA", 313000000);
        pops.put("Canada", 34000000);
        pops.put("Japan", 127000000);
        // Print the HashMap
        System.out.println(pops);
        //Add or edit a value in HashMap
        pops.put("Canada", 32000000);
        //Get value out of HashMap
        Integer JapanPop = pops.get("Japan");
        System.out.println("The population of Japan is: " + JapanPop);
        //Remove a Key Value from HashMap
        pops.remove("USA");
        //Uses a Set to print all Keys in HashMap
        Set<String> myKeys = pops.keySet();
        Collection<Integer> popValues = pops.values();
        System.out.println(myKeys);
        System.out.println(popValues);
```

Lists:
```
    //Create a new list
    List<String> myStringList = new ArrayList<>();
    //add data to the list
    myStringList.add("First");
    myStringList.add("First");
    myStringList.add("Second");
    myStringList.add("Third");

    System.out.println(myStringList);
    //Add to list
    myStringList.add("Fourth");
    //remove from list
    myStringList.remove("First");
    //Use enhanced for loop to iterate through list
    for(String item : myStringList) {
        System.out.println(item);
    }
```

## File I/O
Writing to File:
```
    PrintWriter out = new PrintWriter(new FileWriter("OutFile.txt"));
    out.println("This is a line in my file...");
    out.println("This is a second line in my file...");
    out.println("This is a third line in my file...");
    out.flush(); // forces pending info to write to the file
    out.close();
```

Reading from File:
```
    Scanner sc = new Scanner(new BufferedReader(new FileReader("OutFile.txt")));
    while (sc.hasNextLine()) {
        String currentLine = sc.nextLine();
        System.out.println(currentLine);
    }
```
