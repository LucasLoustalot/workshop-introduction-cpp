# Introduction to C++
The goal of this workshop is to introduce you to some of the features provided by the C++ language, as well as learning part of the Object-Oriented paradigm.

#### Table of Contents
- [Introduction to C++](#introduction-to-c)
      - [Table of Contents](#table-of-contents)
  - [Requirements](#requirements)
  - [Conventions](#conventions)
- [Coming from C](#coming-from-c)
  - [Hello World](#hello-world)
  - [Namespaces](#namespaces)
  - [Streams And Operators](#streams-and-operators)
  - [Memory Management](#memory-management)
  - [References](#references)
  - [Exceptions](#exceptions)
- [Getting Started In Object Oriented Programming](#getting-started-in-object-oriented-programming)
  - [First Step in OOP](#first-step-in-oop)
  - [Constructor / Destructor](#constructor-and-destructor)
  - [A Better Class](#a-better-class)
  - [Heritage](#heritage)
  - [Polymorphism](#polymorphism)
  - [Interface and Abstract Classes](#interface-and-abstract-classes)
- [Going Further](#going-further)
  - [Encapsulating C functions](#encapsulating-c-functions)
  - [Meta programming and Templating](#meta-programming-and-templating)


## Requirements
To complete the workshop, you will need to have a C++ compiler installed.

Usually, **g++** (GNU C++ compiler) will already be present if you are using gcc.

You will need to compile each step independently of one another using **g++**.

## Conventions
While coding in C++ you may use the **CamelCase** naming convention instead of **snake_case**.

# Coming from C

## Hello World

Welcome to the world of C++ programming !

For your first exercise, you must print '*Hello, World*' in the terminal **without using any C functions**.

We expect the following result:
```console
➜ ./a.out
Hello, World!
```

## Namespaces
Namespaces in C++ provide a method for preventing name conflicts and to better organize your code.

Try to find out how it works.

You should write the function `int add(int a, int b)` in a `Math` namespace, then call it from the `main()`.

You should be able to use it like this:
```C++
int main(void) {
    std::cout << "5 + 3 = " << SOMETHING_HERE << std::endl;
    return (0);
}
```
We expect the following result:
```console
➜ ./a.out
5 + 3 = 8
```

## Streams And Operators
You will now learn about operators overloading and streams.

First, create a structure called `Point`; it should contain `int x` and `int y`.

Now, overload an operator to make your point directly printable via the `std::cout` stream.

> [!TIP]
> It might have something to do with the `<<` (*stream*) operator and `std::ostream`.


You should be able to use it like this:
```C++
int main() {
    Point p = {3, 7};

    std::cout << "Le point est : " << p << std::endl;
    return (0);
}
```
We expect the following result:
```console
➜ ./a.out
Le point est : (3, 7)
```

## Memory Management
Allocating objects and variables on the stack is cool.

But as you may know, making a fully-featured program in C without using `malloc` can be a challenge.

In C++, you probably should not use `malloc` since C++ has introduced dedicated operators (like keywords) for dynamic memory management.

Find out what they are, and allocate an `int` and an **array of** `int` on the heap.

Do not use `malloc()` / `free()` or any memory management/allocators functions from the C library.

**Your program must not cause memory leaks** (You can run it with `valgrind` to check).

## References
Passing objects by value can be slow and take a lot of memory.

In C you can use pointers, and while *you can also use pointers in C++* there is a more elegant way: **references**.

Try to learn what the differences are between a **pointer**, a **reference** and passing an object **by value**.

For this exercise, you should write a function called `swap` taking **two ints** as parameters.
This function should swap these two ints.

**You must not use pointers for this !**

You should be able to use it like this:
```C++
int main() {
    int x = 5, y = 10;
    std::cout << "Avant swap: x = " << x << ", y = " << y << std::endl;

    swap(x, y);

    std::cout << "Après swap: x = " << x << ", y = " << y << std::endl;
    return (0);
}
```
We expect the following result:
```console
➜ ./a.out
Avant swap: x = 5, y = 10
Après swap: x = 10, y = 5
```

## Exceptions
Now you will learn about **exceptions**.

Exceptions are a new way to handle an error compared to what you are doing in C.

You should now learn how they work.

Write the following function: `int divide(int a, int b)`.

- **It should not crash your program** in case b is 0.
- **You must use exceptions** and handle the error.

We expect the following result:
```console
➜ ./a.out
10 / 2 = 5
5 / 0 = Erreur : Division par zéro !
```

# Getting Started In Object Oriented Programming

## First Step in OOP

Now that you've had a taste of C++, it's time to dive into **Object-Oriented Programming (OOP)**. OOP is a programming paradigm that uses "objects" to design applications and computer programs. It’s all about creating classes and objects that encapsulate data and behavior.

Let’s start with a simple class: `Student`. This class will have a name and energy level. Your task is to understand how classes work and how to create an object from a class.

You should be able to use it like this:
```cpp
int main() {
    Student student("Lucas");

    student.displayInfo();

    return 0;
}
```
We expect the following result:
```console
➜ ./a.out
Name: Lucas, Energy: 100
```

## Constructor And Destructor

In C++, constructors and destructors are special member functions of a class. A constructor is called when an object is created, and a destructor is called when an object is destroyed.

You should be able to use it like this:
```cpp
int main() {
    Student student("Lucas");

    student.displayInfo();

    return 0;
}
```
We expect the following result:
```console
➜ ./a.out
Student [Lucas]: I'm ready to learn C++.
Name: Lucas, Energy: 100
Student [Lucas]: Wow, much learning today, very smart, such C++.
```

## A Better Class

Now that you understand the basics of classes, let’s make the Student class more realistic. Add methods to allow the student to study and rest, which will affect their energy level.

You should be able to use it like this:
```cpp
int main() {
    Student student("Lucas");

    student.displayInfo();
    student.study(20);
    student.rest(10);
    student.displayInfo();

    return 0;
}
```
We expect the following result:
```console
➜ ./a.out
Student [Lucas]: I'm ready to learn C++.
Name: Lucas, Energy: 100
Lucas is studying and loses 20 energy.
Lucas is resting and gains 10 energy.
Name: Lucas, Energy: 90
Student [Lucas]: Wow, much learning today, very smart, such C++.
```

## Heritage

Inheritance is a key concept in OOP. It allows you to create a new class that is based on an existing class. The new class inherits the attributes and methods of the existing class, and you can add new attributes and methods or override existing ones.

You should be able to use it like this:
```cpp
int main() {
    Student basicStudent("Lucas");
    basicStudent.displayInfo();
    basicStudent.study(20);
    basicStudent.rest(10);
    basicStudent.displayInfo();

    std::cout << "-----------------------------------" << std::endl;

    AdvancedStudent advancedStudent("Emma", "Machine Learning");
    advancedStudent.displayInfo();
    advancedStudent.study(30);
    advancedStudent.rest(15);
    advancedStudent.displayInfo();

    return 0;
}
```

We expect the following result:

```console
➜ ./a.out
Student [Lucas]: I'm ready to learn C++.
Name: Lucas, Energy: 100
Lucas is studying and loses 20 energy.
Lucas is resting and gains 10 energy.
Name: Lucas, Energy: 90
-----------------------------------
Student [Emma]: I'm ready to learn C++.
Advanced Student [Emma]: Specializing in Machine Learning.
Name: Emma, Energy: 100, Specialization: Machine Learning
Emma is studying and loses 30 energy.
Emma is resting and gains 15 energy.
Name: Emma, Energy: 85, Specialization: Machine Learning
Advanced Student [Emma]: Time to master Machine Learning!
Student [Emma]: Wow, much learning today, very smart, such C++.
Student [Lucas]: Wow, much learning today, very smart, such C++.
```

## Polymorphism

Polymorphism allows objects of different classes to be treated as objects of a common superclass. It’s a powerful feature of OOP that enables flexibility and extensibility in your code.

You should be able to use it like this:
```cpp
int main() {
    Student *student1 = new Student("Lucas");
    Student *student2 = new HardworkingStudent("Emma");

    std::cout << "-----------------------------------" << std::endl;

    student1->displayInfo();
    student1->study(20);
    student1->displayInfo();

    std::cout << "-----------------------------------" << std::endl;

    student2->displayInfo();
    student2->study(30);
    student2->displayInfo();

    std::cout << "-----------------------------------" << std::endl;

    HardworkingStudent *hardStudent = dynamic_cast<HardworkingStudent*>(student2);
    if (hardStudent) {
        hardStudent->study(15, "C++ Templates");
    }

    std::cout << "-----------------------------------" << std::endl;

    delete student1;
    delete student2;

    return 0;
}
```

We expect the following result:

```console
➜ ./a.out
Student [Lucas]: I'm ready to learn C++.
Student [Emma]: I'm ready to learn C++.
Hardworking Student [Emma]: Studying is my passion!
-----------------------------------
Name: Lucas, Energy: 100
Lucas is studying and loses 20 energy.
Name: Lucas, Energy: 80
-----------------------------------
Name: Emma, Energy: 100
Emma is studying intensely and loses 30 energy!
Name: Emma, Energy: 70
-----------------------------------
Emma is deeply studying C++ Templates and loses 15 energy!
-----------------------------------
Student [Lucas]: Wow, much learning today, very smart, such C++.
Hardworking Student [Emma]: Time to relax a bit!
Student [Emma]: Wow, much learning today, very smart, such C++.
```

## Interface and Abstract Classes

In C++, an interface is a class that has only pure virtual functions. An abstract class is a class that cannot be instantiated and is meant to be inherited by other classes.

You should be able to use it like this:
```cpp
int main() {
    Learner *learners[2];
    learners[0] = new Student("Lucas");
    learners[1] = new HardworkingStudent("Emma");

    std::cout << "-----------------------------------" << std::endl;

    for (int i = 0; i < 2; i++) {
        learners[i]->learn();
    }

    std::cout << "-----------------------------------" << std::endl;

    for (int i = 0; i < 2; i++) {
        delete learners[i];
    }

    return 0;
}
```

We expect the following result:

```console
➜ ./a.out
Student [Lucas]: I'm ready to learn C++.
Student [Emma]: I'm ready to learn C++.
Hardworking Student [Emma]: Studying is my passion!
-----------------------------------
Lucas is learning something new!
Emma is learning in an advanced way!
-----------------------------------
Student [Lucas]: Wow, much learning today, very smart, such C++.
Hardworking Student [Emma]: Time to relax a bit!
Student [Emma]: Wow, much learning today, very smart, such C++.
```

# Going Further

## Encapsulating C functions

In this part, you are going to create your own encapsulation of the `opendir` / `readdir` / `closedir` C functions to be able to list files in a directory in C++!

Create a `DirectoryLister` class with the following methods:
- `bool open(const std::string& path, bool hidden)`
- `std::string get()`

The following behavior is expected:
- `open`: opens the new directory given as parameter. Returns true on success. In case of failure, the
directory stream becomes invalid, a description of the error (perror) is printed on the standard error
output and the method returns false.
- `get`: returns the name of the next entry in the current directory, or an empty string if the end of the
directory stream is reached or the stream is invalid. Hidden files are ignored when the directory is
opened with the hidden parameter set to false.

Your encapsulation is expected to not leak any `DIR *`.

Provide the **two following constructors**:
- `DirectoryLister()`: creates the class without opening a directory.
- `DirectoryLister(const std::string& path, bool hidden)`: opens the directory with the given parame-
ters.

> [!IMPORTANT]
> You are not allowed to use `std::filesystem`, you **MUST** use `opendir`, `readdir` and `closedir` for this exercise.


You should be able to use it like this:
```cpp
int main(void) {
    DirectoryLister dl("./test/", true);
    for (std::string file = dl.get(); !file.empty(); file = dl.get()) {
        std::cout << file << std::endl;
    }
    dl.open("invalid path", true);
    if (dl.open("./test/", false) == true) {
        for (std::string file = dl.get(); !file.empty(); file = dl.get()) {
            std::cout << file << std::endl;
        }
    }
  return (0);
}
```

We expect the following result (the order of the folders are not important):
```console
➜ ls -a ./test/
.
..
.hidden
subdir
testFile1.txt
testFile2.txt
testFile3.txt

➜ ./a.out
testFile3.txt
..
testFile1.txt
.
subdir
.hidden
testFile2.txt
invalid path: No such file or directory
testFile3.txt
testFile1.txt
subdir
testFile2.txt
```

## Meta programming and Templating

Templates are a way to allow functions and classes to use the same code for many different data types.
This is a very powerfull feature of C++, and it is widely used.

For this part, you should write the following function templates:
- `swap`: swaps the value of its two parameters.
- `min`: returns the smallest of its two parameters.
- `max`: returns the biggest of its two parameters.

These templates should generate functions that can be called with any type of parameter, as long as they
have the same type.

> [!IMPORTANT]
> You are not allowed to use function overloading, you **MUST** the `template` keyword for this exercise.

You should be able to use it like this:
```cpp
int main(void) {
    int ia = 10;
    int ib = 20;
    float fa = 10.0f;
    float fb = 20.0f;

    swap(ia, ib);
    swap(fa, fb);
    std::cout << "ia=" << ia << " ib=" << ib << std::endl;
    std::cout << "fa=" << fa << " fb=" << fb << std::endl;

    std::cout << "Min (int):" << min(ia, ib) << std::endl;
    std::cout << "Min (float):" << min(fa, fb) << std::endl;

    std::cout << "Max (int):" << max(ia, ib) << std::endl;
    std::cout << "Max (float):" << max(fa, fb) << std::endl;

    return (0);
}
```

We expect the following result:
```console
➜ ./a.out
ia=20 ib=10
fa=20 fb=10
Min (int):10
Min (float):10
Max (int):20
Max (float):20
```