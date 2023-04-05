# Process Writeup

## Name: Emmanuel Dorta
## Course: APCSA
## Period: 6
## Concept: Inheritance and Recursion.

### Context.
Over the past few weeks, our class has been learning about and working on Java Class Inheritance and Recursion. 
Unit 9 was the main bulk of Inheritance, including 3 lessons about how Inheritance worked and how you could use it.
Inheritance is all about making classes within other classes that inherit the traits of the parent class.
For example, when you have a main class called parent, and extend this class with a child class, the child can inherit methods from the parent but also have it's own methods or variables separate from the parent.
Inheritance allows for added depth and versatility in many different ways, far separated from just using a singular class.
Recursion is not similar, as recursion is all about having a method recall itself while still _inside_ the method.
This may seemingly break things, or make things infinite, but most recursive methods have a base case. 
A base case is a conditional that assures the method won't be endless, by adding a new check for a specific circumstance. 
For example, lets say we call the method recur(6). All recur() does is add 1 to the given value, until the value reaches 10, in which it returns 10.
Through recursion, the method would be recalled 5 times, once for each number before reaching 10, and once for when it reaches ten and returns 10.
Recursion is all about streamlining a process through base cases and recalling the method in order to get a final answer. 
On paper, its exceedingly slow, but when you get into a rythym then it clicks in.

I personally believe both of these units were quite easy, with their hidden difficulties. 
Inheritance was a nice refresher on the basics of making classes after a while, it included very nice concepts and activities to learn and recall some basics of Java again.
Recursion was, definitely a concept, while not difficult on paper, it felt excessive and a bit too long at times. 
Trying to do recursion on paper is annoying, but still doable and once you get the hang of it, it becomes a bit easier. 

### Going Over Unit 9, Lesson 1, Coding Activity 1.
This Coding Activity requires you to create an extending class called SpecialityCoffee, extending the Coffee class and having a new variable called flavor.
You are then required to make 3 methods, all of which are constructor methods and one toString method.
The activity was actually really easy, it was mainly the fact there were multiple constructor methods that worked oddly that was the main issue.
Otherwise, it should be easy to go over.
First and foremost, we'll set up the class itself, our flavor variable and the first constructor for the class.

```Java
public class SpecialityCoffee extends Coffee{
  
  private String flavor;
  
  public SpecialityCoffee(){
    super();
    flavor = "vanilla";
  }
}
```
Using extends allows us to access any methods of the parent class, in this case Coffee. Which we immediately use in our first constructor.
Since this constructor has no variables, we call the Coffee class constructor that also has no variables. We can do this by calling super(), which accesses the constructor of the parent class.
We then set the flavor to "vanilla" as the prompt asks us to do. 
Next we will implement a constructor with actual parameters, and it is actually very similar to this constructor.

```Java
public SpecialityCoffee(String size, String type, String taste){
  super(size, false, 1, type);
  flavor = taste;
}
```
Again, this was relatively easy. In this constructor, we call the parent constructor with variables. 
This is much like calling a method outside of both classes. By inputting variables, we create and set those variables just like if we had done it outside of either class.
A slight difference here is the implementation of 1 and type, which have to be included as base variables due to the fact no constructor in the parent class has only 2 variables. 
We also set flavor to taste, as per the prompts request.
Our next task is to finish our constructors with filling out every single parameter and variable, which is really easy.

```Java
public SpecialityCoffee(String size, boolean isSkinny, int shots, String type, String taste){
  super(size, isSkinny, shots, type);
  flavor = taste;
}
```
This finishes out all of our constructors of the SpecialityCoffee class, using super to call the parent constructor. However, we do have to make the toString for this class.
Which is actually a unique case of using super.

```Java
public String toString(){
  return super.toString() + " with " + flavor;
}
```
Here we see that super is used under a different context.
As stated before, the child class inherits all the available methods of the parent class, not just the constructor method.
Using .toString on super, allows us to call that method from the parent class and have its value returned here instead of the parent class.
This is known as overriding, where the child class overrides a specific method of the parent class a specific situation, in order to return a specific response.

Thats the end of this Coding Activity, as I said there were no difficulties here nor for the rest of the unit. 
I really had a handle on the entire unit, and felt at home with how to use child classes and inheritance in general.
Now we can move on to recursion, with another pretty easy Coding Activity, though both of these still ended up with some takeaways I'll share at the end.

### Unit 10, Lesson 1, Coding Activity 1.
As mentioned, this unit is all about recursion. So activity 1 is all about teaching the basics of how recursion will return specific methods in a String format.
To begin, this prompt asks us to debug the printUpToEnd method.
The purpose of this method is, when given a positive integer, to print every positive integer up to and including the variable that ends with the same digit, excluding 0.
So for example, if we submit `printUpToEnd(51);`, the method should return `1 11 21 31 41 51`.
So lets look at what we get and check from there.

```Java
public static void printUpToEnd(int n)
{
  System.out.print(n + " ");
  if (n != 0)
  {
    printUpToEnd(n);
  }
}
```
So here we can see what we have to debug.
The method starts by returning the variable given, the opposite of what should be returned by the methods standards.
So moving the print call should be noted. Our next important issue is the conditional.
The base case here checks if n is not 0, then recalling the method with the exact same variable of n.
This would mean that the method would infinitely loop, because nothing is done to change the given variable.
Knowing this, lets make some changes to influence further thinking and exploration for debugging the recursive method.

```Java
public static void printUpToEnd(int n)
{
  if(n-10 > 0){
    printUpToEnd(n-10);
  }
  System.out.print(n + " ");
}
```
Here is the final version of my solution, which includes every step I needed to take mentioned previously. Let's go over each one now.
First off is moving the print call to after the conditional, which means that the method only starts to print out values after the entire recursive loop is done.
Next is the conditional, which previously only checked if the variable n was not 0. This time, we check if n minus 10 is greater than 0.
The negative 10 here is added so that our variable never goes below 0, as in the case where minus 10 isn't there, we accidentally printed out -9 when we should only print positive integers.
If the conditional is true, we then recall the method, with n minus 10 inside the recall. 
This will slowly decrease the value of n, until it reaches 1, if we consider `printUpToEnd(51);`.
With this, we solemnly finish out the Coding Activity, with a clean 100 and a smile of personal approval and self-growth.

### Takeaways and Special Thanks
In this section, I would like to explain some of my takeaways that I had not mentioned before:

- For inheritance, the most important thing to remember is that you cannot directly access parent variables, thus calling the constructor and any other methods is important to succeed with child classes.
- For recursion, depending on the order you wish to return values in, you'll have to change the position of your print call. If you want to return a descending order, put the print call first, before the conditional, and ascending order can have the print call after the conditional.
Its actually quite confusing for how to directly print values, so this detail is important for some cases of recursion.

Finally, I would like to give thanks to you. The journey of APCSA has been a long one, there have been many challenges and difficulties, but with you there to read these writeups, I feel at peace with myself.
Thank you for the time, and I hope you have enjoyed reading my sometimes incoherent ramblings and moments of self-reflection. 
Have a wonderful day.
