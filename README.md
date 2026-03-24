# Oops-Module-3
# Ex.No:3(A) INHERITANCE AND AGGREGATION

## QUESTION:
A jewelry store tracks gold rates for different types of customers. The base class is Customer with attributes like customerId, name, and purchaseWeight (in grams). There are two types of customers: RegularCustomer and PremiumCustomer. RegularCustomer gets a fixed discount of 2% on the gold rate per gram. PremiumCustomer gets a 5% discount plus a special cashback. The base gold rate per gram is input at runtime. For each customer, calculate the final price they pay:

finalPrice = purchaseWeight * (goldRatePerGram - discount)

For PremiumCustomer, additionally show cashback amount (which is 1% of the final price).

## AIM:
To develop a Java program that calculates the final gold purchase amount for different customer types using inheritance.  
The program should apply:
- **2% discount** for RegularCustomer  
- **5% discount + 1% cashback** for PremiumCustomer  
and compute the final payable amount based on purchase weight and gold rate per gram.

## ALGORITHM :
1. Create a base class **Customer** with attributes:
   - `customerId`
   - `name`
   - `purchaseWeight`
   - `goldRatePerGram`
2. Implement a constructor to initialize the above values.
3. Create a method `getDiscountRate()` that returns `0` in the base class.
4. Create a method `calculateFinalPrice()`:
   - Calculate discount amount  
   - Subtract discount from gold rate  
   - Multiply effective rate with purchase weight  
5. Create a `display()` method to print customer details.
6. Create **RegularCustomer** class extending Customer:
   - Override `getDiscountRate()` to return **2%**
   - Override `display()` to show details
7. Create **PremiumCustomer** class extending Customer:
   - Override `getDiscountRate()` to return **5%**
   - Add `getCashback()` returning **1% of final price**
   - Override `display()` to show details including cashback
8. In the `main()` method:
   - Read user input (type, id, name, weight, gold rate)
   - Based on type, create the appropriate customer object  
   - Call `display()` to print output
9. End the program.

## PROGRAM:
  ```
/*
Program to implement a conditional statement using Java
Developed by: Harshada P K
RegisterNumber:  212224060097
*/
```

## SOURCE CODE:
```
import java.util.Scanner;
import java.text.DecimalFormat;

class Customer {
    String customerId, name;
    double purchaseWeight, goldRatePerGram;

    Customer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        this.customerId = customerId;
        this.name = name;
        this.purchaseWeight = purchaseWeight;
        this.goldRatePerGram = goldRatePerGram;
    }

    int getDiscountRate() {
        return 0;
    }

    double calculateFinalPrice() {
        double discountAmount = goldRatePerGram * getDiscountRate() / 100.0;
        return purchaseWeight * (goldRatePerGram - discountAmount);
    }

    void display(String type) {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: " + type);
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: " + getDiscountRate() + "%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
    }
}

class RegularCustomer extends Customer {
    RegularCustomer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        super(customerId, name, purchaseWeight, goldRatePerGram);
    }

    int getDiscountRate() {
        return 2;
    }
}

class PremiumCustomer extends Customer {
    PremiumCustomer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        super(customerId, name, purchaseWeight, goldRatePerGram);
    }

    int getDiscountRate() {
        return 5;
    }

    double calculateCashback() {
        return calculateFinalPrice() * 0.01;
    }

    void display(String type) {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: " + type);
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: " + getDiscountRate() + "%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
        System.out.println("Cashback: " + df.format(calculateCashback()));
    }
}
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String customerType = sc.nextLine().trim(); 
        String customerId = sc.nextLine();
        String name = sc.nextLine();
        double purchaseWeight = Double.parseDouble(sc.nextLine());
        double goldRate = Double.parseDouble(sc.nextLine());

        if (customerType.equalsIgnoreCase("Premium")) {
            PremiumCustomer p = new PremiumCustomer(customerId, name, purchaseWeight, goldRate);
            p.display("Premium"); 
        } else if (customerType.equalsIgnoreCase("Regular")) {
            RegularCustomer r = new RegularCustomer(customerId, name, purchaseWeight, goldRate);
            r.display("Regular");
        } else {
            Customer c = new Customer(customerId, name, purchaseWeight, goldRate);
            c.display("Standard");
        }

        sc.close();
    }
}
```

## OUTPUT:
<img width="832" height="701" alt="image" src="https://github.com/user-attachments/assets/80fdf85b-2b42-4187-a689-ee5603a70f52" />

## RESULT:
The program successfully computes the final gold purchase price for:
- General customers  
- Regular customers (with 2% discount)  
- Premium customers (with 5% discount and 1% cashback)

It displays complete details including customer type, discount applied, final price, and cashback for premium customers.


# Ex.No:3(B) POLYMORPHISM

## QUESTION:
Write a Java program using method overloading to print student details. Create a class Student with:

- print(String name)

- print(String name, int age)

- print(String name, int age, String dept)

## AIM:
To write a Java program that demonstrates method overloading by printing student details using three versions of the `print()` method with different parameter lists.

## ALGORITHM :
1. Create a class `Student` with three overloaded static methods:
   - `print(String name)`
   - `print(String name, int age)`
   - `print(String name, int age, String dept)`
2. In the `main` method:
   - Create a `Scanner` object to read input.
   - Read a name and call `print(name)`.
   - Read a name and age, then call `print(name, age)`.
   - Read a name, age, and department, then call `print(name, age, dept)`.
3. Each method prints the student details according to the parameters provided.
4. End the program.

## PROGRAM:
  ```
/*
Program to implement a conditional statement using Java
Developed by: Harshada P K
RegisterNumber:  212224060097
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class Student {
    public static void print(String name) {
        System.out.println("Name: " + name);
    }

    public static void print(String name, int age) {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void print(String name, int age, String dept) {
        System.out.println("Name: " + name + ", Age: " + age + ", Dept: " + dept);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String name1 = scanner.nextLine();
        print(name1);

        String name2 = scanner.nextLine();
        int age2 = scanner.nextInt();
        scanner.nextLine(); 
        print(name2, age2);

        String name3 = scanner.nextLine();
        int age3 = scanner.nextInt();
        scanner.nextLine();
        String dept3 = scanner.nextLine();
        print(name3, age3, dept3);
    }
}
```

## OUTPUT:
<img width="850" height="603" alt="image" src="https://github.com/user-attachments/assets/a78d9cb1-9f34-4ec6-a285-fc784d35ee62" />

## RESULT:
The program successfully demonstrates method overloading by printing student details using three different method signatures based on the number of arguments passed.


# Ex.No:3(C) ABSTRACTION

## QUESTION:
Create abstract class GameScore with method finalScore().  
Subclasses:
ArcadeGame: score = baseScore + (level × 100)
PuzzleGame: score = (attempts ≤ 3) ? 1000 - (attempts × 100) : 500

## AIM:
To write a Java program that uses an abstract class to calculate final game scores for two types of games:  
ArcadeGame and PuzzleGame, each implementing its own scoring logic.

## ALGORITHM:
1. Create an abstract class `GameScore` with the abstract method `finalScore()`.
2. Create subclass `ArcadeGame` with:
   - Attributes: `base`, `level`
   - Scoring rule: `finalScore = base + (level × 100)`
3. Create subclass `PuzzleGame` with:
   - Attribute: `attempts`
   - Scoring rule:
     - If attempts ≤ 3 → `finalScore = 1000 - (attempts × 100)`
     - Else → `finalScore = 500`
4. In the `main` method:
   - Read `type` (1 for ArcadeGame, 2 for PuzzleGame)
   - If `type == 1`:
     - Read `base` and `level`
     - Create `ArcadeGame` object
   - Else:
     - Read `attempts`
     - Create `PuzzleGame` object
   - Call `finalScore()` and print the result.
5. End the program.

## PROGRAM:
 ```
/*
Program to implement a conditional statement using Java
Developed by: Harshada P K
RegisterNumber:  212224060097
*/
```

## SOURCE CODE:
```
import java.util.*;
abstract class Game
{
    abstract int finalScore();
}
class Arcade extends Game
{
    int base;
    int level;
    Arcade(int base,int level)
    {
        this.base=base;
        this.level=level;
    }
    int finalScore()
    {
        return base+(level*100);
    }
}
class Puzzle extends Game
{
    int att;
    Puzzle(int att)
    {
        this.att=att;
    }
    int finalScore()
    {
        return (att<=3)?1000-(att*100):500;
    }
}
public class main
{
    public static void main(String[] args)
    {
        Scanner input=new Scanner(System.in);
        int type=input.nextInt();
        if(type==1)
        {
            int base=input.nextInt();
            int level=input.nextInt();
            Arcade a=new Arcade(base,level);
            System.out.println(a.finalScore());
        }
        else if(type==2)
        {
            int att=input.nextInt();
            Puzzle p=new Puzzle(att);
            System.out.println(p.finalScore());
        }
    }
}
```

## OUTPUT:
<img width="354" height="206" alt="image" src="https://github.com/user-attachments/assets/c7d29ada-3636-4732-847f-28a95ba50bc8" />

## RESULT:
The program successfully calculates and displays the final score based on game type and user input using abstract methods and dynamic method dispatch.


# Ex.No:3(D) INTERFACE 

## QUESTION:
Two types of traffic controllers decide whether a vehicle can pass based on signal color. The decision logic varies by controller.
AggressiveController: Allows only if "GREEN".
DefensiveController: Allows for "GREEN" or "YELLOW".

## AIM:
To develop a Java program that decides whether a vehicle can move or must stop based on the signal color and the type of traffic controller (Aggressive or Defensive) using interfaces.

## ALGORITHM :
1. Define an interface `TrafficController` with the method:
   - `boolean canGo(String signalColor)`
2. Create class `AggressiveController` implementing the interface:
   - Allows passage only if the signal color is GREEN.
3. Create class `DefensiveController` implementing the interface:
   - Allows passage if the signal color is GREEN or YELLOW.
4. In the `main` method:
   - Read `color` (signal color)
   - Read `type` (controller type: 1 or 2)
5. Based on `type`:
   - If 1 → create `AggressiveController`
   - Else → create `DefensiveController`
6. Call `canGo(color)` to check permission.
7. If true → print `"GO"`
   - Else → print `"STOP"`
8. End the program.

## PROGRAM:
  ```
/*
Program to implement a conditional statement using Java
Developed by: Harshada P K
RegisterNumber:  212224060097
*/
```

## SOURCE CODE:
```
import java.util.*;
interface Vehicle
{
    String predict(String color);
}
class AggressiveController implements Vehicle
{
    public String predict(String color)
    {
        if(color.equals("GREEN"))
        {
            return "GO";
        }
        else
        {
            return "STOP";
        }
    }
}
class DefensiveController implements Vehicle
{
    public String predict(String color)
    {
        if(color.equals("GREEN ")|| color.equals("YELLOW"))
        {
            return "GO";
        }
        else
        {
            return "STOP";
        }
       
    }
}
public class main
{
    public static void main(String[] args)
    {
        Scanner input=new Scanner(System.in);
        String color=input.next();
        int type=input.nextInt();
        Vehicle bot;
        if(type==1)
        {
            bot=new AggressiveController();
        }
        else
        {
            bot=new DefensiveController();
        }
        System.out.println(bot.predict(color));
    }
}

```

## OUTPUT:
<img width="431" height="202" alt="image" src="https://github.com/user-attachments/assets/893c86c5-b2f8-4240-8d2b-98ca05b093a6" />

## RESULT:
The program successfully determines whether a vehicle can move based on the signal color and controller type using interface-based polymorphism.

# Ex.No:3(E) INNER CLASS 
### ENUM

## QUESTION:
Write a Java program to define an enum named GameLevel with three constants: EASY, MEDIUM, and HARD.

## AIM:
To write a Java program that defines an enum named GameLevel with constants EASY, MEDIUM, and HARD, and allows the user to select a game level.

## ALGORITHM :
1. Define an enum GameLevel with constants: EASY, MEDIUM, HARD.

2. Read user input as a string and convert it to uppercase.

3. Use GameLevel.valueOf() to match the input with an enum constant.

4. If the value matches, print the selected game level.

5. If no match is found, catch IllegalArgumentException and show an error message.

6. Close the scanner in the finally block.




## PROGRAM:
 ```
/*
Program to implement a conditional statement using Java
Developed by: Harshada P K
RegisterNumber:  212224060097
*/
```


## SOURCE CODE:
```
import java.util.*;
enum GameLevel
{
    EASY,MEDIUM,HARD;
}
public class main
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.in);
        String input=sc.nextLine().toUpperCase();
        GameLevel game=GameLevel.valueOf(input);
        System.out.println("You selected game level: "+game);
        
    
    }
}
```




## OUTPUT:
<img width="805" height="188" alt="514369907-fe75fd02-00e4-4672-8233-93e35f565e9f" src="https://github.com/user-attachments/assets/d54c3ab4-1f3f-4824-9f96-938190b73b16" />



## RESULT:
The program has been executed successfully and the desired output has been obtained.

# Ex.No:3(F) WRAPPER CLASS

## QUESTION:
Write a Java program to find the square root of a number using Double wrapper class.

## AIM:
To write a Java program that reads a number in string format, converts it into a double, and prints its square root using the `Math.sqrt()` function.

## ALGORITHM :
1. Start the program.
2. Create a `Scanner` object to read input from the user.
3. Read a string value representing a number.
4. Convert the string to a `Double` using `Double.parseDouble()`.
5. Use `Math.sqrt()` to compute the square root of the number.
6. Display the result in the required format.
7. End the program.

## PROGRAM:
 ```
/*
Program to implement a conditional statement using Java
Developed by: Harshada P K
RegisterNumber:  212224060097
*/
```


## SOURCE CODE:
```
import java.util.*;

public class Main
{
    public static void main(String[] args)
    {
        Scanner s = new Scanner(System.in);
        String str = s.next();
        
        Double num = Double.parseDouble(str);
        System.out.println("Square root of "+num+" is: "+(Math.sqrt(num)));
    }
}
```

## OUTPUT:
<img width="741" height="233" alt="image" src="https://github.com/user-attachments/assets/e890e0d1-6301-45de-ba69-890c05df00ba" />

## RESULT:
The program successfully reads a numeric string, converts it to a double value, computes its square root, and displays the result.

