# Accessor Methods and Mutator Methods

## Learning Goals

- Explain Accessor Methods
- Explain Mutator Methods
- Discuss IntelliJ Features

## Introduction

We have heard of accessor methods before in the Access Modifiers Lesson.
Access methods and mutator methods are instance methods but hold an
important purpose when accessing private instance variables. Let us
dive more into what these methods are and how they are useful!

## Accessor Methods

An **accessor method** is a public method that is used to retrieve the contents
of a private instance variable. This means that the return type will be the
same type as the private instance variable of interest. Accessor methods
are also referred to as **getters** as the method name conventionally starts
with the word "get".

Let's review the `Student` class again and see how we could get the first
name of the student using an accessor method.

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.major = "Undeclared";
    }
    
    public Student(String firstName, String lastName, String major) {
       this(firstName, lastName);
       this.major = major;
    }

    public String getFirstName() {
       return firstName;
    }
}
```

In the code above, we see that we defined the accessor method `getFirstName()`.
Again, it is a convention in Java to use the word "get" in the accessor method
name. This method will return the `String` value of the variable
`firstName`. This is helpful in case a `Student` object is defined in another
class, and it wants to know the `firstName` of the `Student`.

## Mutator Methods

A **mutator method** is a public method that is used to set the contents of a
private instance variable. Unlike accessor methods, it will not return anything,
so it will have the `void` return type. But it will take in a parameter to
assign the variable appropriately. The parameter should have the same type as
the private instance variable of interest. Usually it will also have the same
variable name as well. Mutator methods are also referred to as **setters** as
the method name conventionally starts with the word "set".

In our `Student` class, we have a `major` attribute that can be defaulted to
the value of `undeclared`. But what if the student eventually decides to
declare a major? We don't want to re-construct the `Student` object. Instead,
we can use a mutator method!

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.major = "Undeclared";
    }
    
    public Student(String firstName, String lastName, String major) {
       this(firstName, lastName);
       this.major = major;
    }

    public String getFirstName() {
       return firstName;
    }
    
    public void setMajor(String major) {
        this.major = major;
    }
}
```

In the code above, we see that we defined the mutator method `setMajor()`.
Again, it is a convention in Java to use the word "set" in the mutator method
name. This method will make use of the `this` keyword again to assign the
instance variable to the local variable that came in as a parameter. We can
now use this method to set a `major` on a `Student` object even after the
object has been constructed.

Let's add getters and setters to the rest of the private instance variables,
as this is typically a good practice to follow when creating a class.

## Accessor Methods and Mutator Methods in IntelliJ

The nice thing about using the IntelliJ IDE is that the IDE can actually help
us generate these accessor and mutator methods a little quicker.

In IntelliJ, if you right-click on the instance variable, you will be prompted
with this menu:

![generate-method](https://curriculum-content.s3.amazonaws.com/java-mod-1/accessor-methods/Generate-Method.png)

When in that menu, click on the `Generate...` option or use the keyboard
shortcut of `Alt+Insert`.

Once you are there, a few more options are listed out. These are different
methods that we could generate! Let's start with adding a getter to the
`major` attribute. To do so, click on `Getter` from the option list. It will
then create the accessor method needed for the `major` variable!

![generate-getter](https://curriculum-content.s3.amazonaws.com/java-mod-1/accessor-methods/Generate-Getter-IntelliJ.png)

We can perform the same operation on the `firstName` attribute to create a
setter method. Perform the right-click operation again. But this time instead
of clicking on the `Getter` option from the list, select the `Setter` option.
This will create the mutator method needed for the `firstName` variable.

![generate-setter](https://curriculum-content.s3.amazonaws.com/java-mod-1/accessor-methods/Generate-Setter-IntelliJ.png)

We haven't even touched our `lastName` attribute. Both the getter and the setter
methods need to be added to the `Student` class still. We can actually generate
both those methods at once through IntelliJ! Perform the right-click
operation one last time. This time, we will select the `Getter and Setter`
option from the `Generate` option list. This will create both the accessor and
the mutator methods needed for the `lastName` variable.

![generate-getter-setter](https://curriculum-content.s3.amazonaws.com/java-mod-1/accessor-methods/Generate-Getter-Setter-IntelliJ.png)

Typically, when we create getters and setters, we will want to organize them in
a certain way in our code. How to exactly organize them can be debated. But the
consensus is to keep the getters and setters for each instance variable
together. So the `Student` class may look like this:

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.major = "Undeclared";
    }
    
    public Student(String firstName, String lastName, String major) {
       this(firstName, lastName);
       this.major = major;
    }

    public String getFirstName() {
       return firstName;
    }
    
    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }
    
    public String getLastName() {
        return lastName;
    }
    
    public void setLastName(String lastName) {
        this.lastName = lastName;
    }
    
    public String getMajor() {
        return major;
    }
    
    public void setMajor(String major) {
        this.major = major;
    }
}
```
