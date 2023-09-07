# Compound Assignment Operators

In math, the equation `x = x + 1` would never make sense. A computer interprets the equals sign differently, being assignment instead of actual equality, and so it is actually able to make some sense out of this. Let's look at what it does to process this statement.

---

## 'Recursive' Variable Assignment

In java, our variables often hold information that will change frequently. We looked at a problem in class where a program used a variable called `count` that counted the number of people who got a certain score in a game. As humans, we might think of this as a final, total number. If we break it down into steps though, as a human we would check each individual and *add* them to our total if they met the criteria. This would result in the same total number, but we would have slowly counted up to it. This is how a computer would often handle this, and so we want to value of the variable to change consistently, but we want it to change based on it's previous value. That is, we want it to take its previous value, and modify it by increasing it.

We refer to this as 'recursive' variable assignment, where we assign a new value to a variable based on its previous value. Let's look at this in a sample from `NotesRecursive1.java`:

```java
int count = 5;
System.out.println(count);
count = count + 1;
System.out.println(count);
```

The first line of this file is `int count = 5`, is just a variable declaration and initialization from our last section. Our computer is now storing the number `5` under the codename `count`.

The second line of this file is `System.out.println(count)`. We never explicitly said this, but a print statement can take a variable and it will just print out it's value, so when we run this line we expect to see `5` printed out on the console.

The third line is just like our initial example of `x = x + 1` but now it is with our variable `count` to be `count = count + 1`. In the last section we discussed the idea of **operator precedence**, which is the computer's version of the order of operations in math. Importantly, we have two operations here: addition `+` and assignment `=`. Operator precedence in Java says that addition will come first, and then the assignment. Here are the steps the computer would take to determine what's going on here:

```
count = count + 1       This is our original code.
count = 5 + 1           We need to add, but we need to substitute a value of count to actually add,
                        so we take the current value of 5.
count = 6               We now added up to 6. Assignment says to erase the old value for count
                        and replace it with this new value of 6.
```

We can see with these steps that the computer substitutes the current value of `count`, does the math, and then saves a new value of `count` over the old one.

Now in the fourth line, the print statement is the same as the second line, but the value of the variable has changed so now it should print out `6` in the console.

Try running `NotesRecursive1.java` to see it happen! When we run it, we see the following output:

```
5
6
```

We could have done this process with any of our core operations and with any value, so it's not limited to just adding one. Here are some samples from `NotesRecursive2.java`:

```java
int math = 17;
System.out.println(math);
math = math + 5;
System.out.println(math);
math = math - 4;
System.out.println(math);
math = math * 2;
System.out.println(math);
math = math / 4;
System.out.println(math);
math = math % 3;
System.out.println(math);
```

Each time, it uses the previous value of the variable `math` to calculate a new one with the given operation, and then saves that new value for future calculations. Running this file, we can watch the value change:

```
17
22
18
36
9 
0
```

This is really powerful, but it might get annoying writing our variable twice every time we want to change it's value with an operator, that's where **compound assignment operators** come into play.

---

## Compound Assignment Operators

When we want to change the value of a variable using an operation, we can use a **compound assignment operator**, which is a single operator made up of two characters. The basic structure of these operators is to put the arithmetic operator we are using (`+`, `-`, `*`, `/`, `%`), and then an equals sign, creating `+=`, `-=`, `*=`, `/=`, `%=`. Let's look at how these are used via a sample in `NotesCompound1.java`, which contains code that works exactly the same as our previous example from `NotesRecursive2.java`:

```java
int math = 17;
System.out.println(math);
math += 5;
System.out.println(math);
math -= 4;
System.out.println(math);
math *= 2;
System.out.println(math);
math /= 4;
System.out.println(math);
math %= 3;
System.out.println(math);
```

We can make direct comparisons to `NotesRecursive2.java` to tell how this works. Originally it was `math = math + 5` and now it is `math += 5`, which functionally do the same thing. We often use these compound assignment operators to do this basic arithmetic on a variable more simply.

---

## Incrementing and Decrementing

Going back to our `count` example. We will often want to increase or decrease a variable by 1 in our programs, and now with our compound assignment operators we can see we have a faster way of doing that. Here is a sample from `NotesIncDec1.java` that shows the original and new ways to do it:

```java
int count = 5;
System.out.println(count);
count = count + 1;
System.out.println(count);
count = count - 1;
System.out.println(count);
count += 1;
System.out.println(count);
count -= 1;
System.out.println(count);
```

This is a nice way to tidy it up, but this is something we do so often in programming that we want an even faster way to do it. To do this, we have the increment `++` and decrement `--` operators that add 1 and subtract 1 from a variable respectively. Here is a sample from `NotesIncDec2.java` that shows the normal compound operators and the new increment/decrement operators:

```java
int count = 5;
System.out.println(count);
count += 1;
System.out.println(count);
count -= 1;
System.out.println(count);
count++;
System.out.println(count);
count--;
System.out.println(count);
```

The increment and decrement operators can make our lives so much easier as we increase or decrease variables, but it is important to remember that they only work by 1 at a time, so if we needed to count by 2s or otherwise, we should use our typical compound assignment operators.

---

## Final Notes

Taking our very first example from `NotesRecursive1.java`, the whole file looks like this:

```java
public class NotesRecursive1 {
    public static void main (String[] args){
        int count = 5;
        System.out.println(count);
        count = count + 1;
        System.out.println(count);
    }
}
```

We only honed in on the middle line with our variables initially, but every piece of this file is important to the program running and doing what we want. Taking a look at our second example from `NotesRecursive2.java`, that whole file looks like this:

```java
public class NotesRecursive2 {
    public static void main (String[] args){
        int math = 17;
        System.out.println(math);
        math = math + 5;
        System.out.println(math);
        math = math - 4;
        System.out.println(math);
        math = math * 2;
        System.out.println(math);
        math = math / 4;
        System.out.println(math);
        math = math % 3;
        System.out.println(math);
    }
}
```

Comparing the first two lines of code from both files should feel extremely similar, with only a slight variation. All of our Java files for the foreseeable future will have this structure. The first line is `public class NameOfFileHere{`, where you'll notice that in both examples, it utilizes the name of the file without the `.java` extension. The second line is identical in both cases as `public static void main (String[] args){`.

Throughout the year we will end up unpacking these lines and better understand how they work to better use them to our advantage. For the time being though, we will let Visual Studio Code autofill those lines when we create a Java file and understand that it's on the third line where we put our code using things like our variable statements.

---

## Assignment

Now that you have gone through the notes for this section, you can check out the `Try.md` and `Try.java` files to try a short assignment using this material.
