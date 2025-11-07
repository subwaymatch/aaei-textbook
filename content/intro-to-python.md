# Introduction to Python

Welcome to the world of Python! Python is a versatile, high-level programming language known for its readability and simple syntax. This makes it an excellent choice for beginners and a powerful tool for experts. In this chapter, we'll cover some of the absolute basics to get you started on your programming journey.

![Python Logo Cover Image](images/intro-to-python-cover.png)

## 🐣 What is Python?

Python was created by Guido van Rossum and first released in 1991. Its design philosophy emphasizes code readability, and its syntax allows programmers to express concepts in fewer lines of code than might be used in languages like C++ or Java.

Python is an **interpreted language**, which means that you can run each line of code as you write it, making it great for learning and experimenting. It's used in a wide range of applications, including:

- Web Development
- Data Science and Machine Learning
- Scientific Computing
- Automation and Scripting
- Game Development

:::{note} 🐍 Fun Fact: It's Not About the Snake!
Contrary to what many believe, Python is not named after the reptile. Guido van Rossum was a big fan of the British comedy group _Monty Python's Flying Circus_, and he wanted a name that was short, unique, and a little mysterious. This playful origin is a good reminder that programming can be fun and creative!
:::

### The Zen of Python

The Zen of Python is a collection of guiding principles for writing computer programs in Python. You can access it by typing `import this` in a Python interpreter. Here are a few key principles:

```
>>> import this

The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Readability counts.
...
```

## 🌟 Core Features of Python

- **Readable syntax**: Code is easy to write and understand.
- **Dynamically typed**: You don't need to declare variable types explicitly.
- **Object-oriented**: Everything in Python is an object.
- **Cross-platform**: Runs on Windows, macOS, Linux, and many embedded systems.
- **Extensive libraries**: Rich ecosystem for analytics, AI, web apps, and more.

## 📜 A Brief History of Python

- **Late 1980s**: Guido van Rossum started working on Python at Centrum Wiskunde & Informatica (CWI) in the Netherlands.
- **1991**: The first official release of Python (version 0.9.0) included functions, exceptions, and core data types.
- **2000**: Python 2.0 was released, adding list comprehensions and garbage collection.
- **2008**: Python 3.0 was released, a major redesign to remove inconsistencies (though it was initially controversial).
- **Today**: Python 3 is the standard. Python 2 reached end of life in 2020.

## 🌍 Python Ecosystem

Python's power comes from its huge ecosystem of libraries and frameworks:

- **Data Science & AI**: NumPy, Pandas, Matplotlib, scikit-learn, TensorFlow, PyTorch.
- **Web Development**: Django, Flask, FastAPI.
- **Automation & Scripting**: Selenium, BeautifulSoup.
- **Finance & Business**: QuantLib, Zipline, openpyxl.
- **Scientific Computing**: SciPy, SymPy, Jupyter Notebooks.

---

## ⚖️ Python Compared to Other Languages

### 🖥️ Python vs. C

- **C** is lower-level, closer to the machine, and much faster for system-level programming.
- **Python** is higher-level, focusing on readability and ease of use, but generally slower.

### ☕ Python vs. Java

- **Java** requires explicit type declarations and has a more verbose syntax.
- **Python** uses dynamic typing and concise syntax, making it easier for beginners.
- Both are object-oriented and cross-platform, but Python is often preferred for rapid prototyping.

### 📊 Python vs. R

- **R** is specialized for statistics and data visualization.
- **Python** is more general-purpose. Additionally, Python has powerful machine learning and deep learning libraries (TensorFlow, PyTorch, Keras, etc.) that make it a strong competitor in data science.

### 🌐 Python vs. JavaScript

- **JavaScript** dominates web development in the browser.
- **Python** dominates in data analytics, AI, and backend web development (e.g., Django, Flask).
- Both have vibrant ecosystems, but they serve slightly different purposes.

---

## 💪 Strengths of Python

- Easy to learn and beginner-friendly.
- Extremely versatile and widely adopted.
- Huge community support and rich ecosystem.
- Strong presence in cutting-edge fields like AI and data science.

## ⚠️ Limitations of Python

- Slower than compiled languages (C, C++).
- Not ideal for mobile app development.
- Dynamic typing can lead to runtime errors if not carefully managed.
- High memory usage compared to lower-level languages.

---

## 🎯 Why Learn Python?

- It is one of the **easiest languages for beginners**.
- It is **versatile**, being used in web development, automation, AI, data analysis, finance, and more.
- It has an **enormous community**, meaning plenty of tutorials, forums, and libraries are available.
- Skills in Python are **highly valued in the job market**.

---

## ⚙️ How Python Executes Your Code

To understand how the Python interpreter executes your code, we first need to understand *expression*s in the context of programming.

An expression is a syntatic entity that may be _evaluated_ to determine its value ([source](<https://en.wikipedia.org/wiki/Expression_(computer_science)>)). Here is a simple expression.

$$
1 + 2
$$

The mathematical expression above *evaluate*s to the value $3$.

Expressions are not always as simple as having two operands and a single operator. Sometimes, you may have an expression that contains multiple *sub-expression*s. Look at this mathematical expression.

$$
(1 + 2) \times (4 \div 2)
$$

We are trained to perform the arithmetic operations in the predefined order of operations ([PEMDAS](https://www.khanacademy.org/math/cc-sixth-grade-math/cc-6th-arithmetic-operations/cc-6th-order-of-operations/v/more-complicated-order-of-operations-example)). Here is a step-by-step breakdown of how a human would carry out this evaluation process.

1. Evaluate $(1 + 2)$ to $3$,
2. Evaluate $(4 \div 2)$ to $2$,
3. Rewrite the equation to $3 \times 2$,
4. Evaluate $3 \times 2$ to $6$

Python executes your program in a similar fashion. It evaluates your expressions from left to right (except when you're performing an assignment operation, which we will discuss later). The operator precedence also emulates the mathematical order of operations, except that there are some operators that only exist in Python.

For a summary of the operator precedence in Python, refer to the **Operator Precedence** section of https://docs.python.org/3/reference/expressions.html.

---

## 💬 Python Comments

Python comments are lines in your code that are not executed. They are used to explain and clarify the code for anyone reading it (including your future self). In Python, comments start with the `#` symbol.

```python
# This is a single-line comment
print("Hello, World!")
```

```python
print("Hello, World!")  # This is another comment
```

```python
# This is a multi-line comment
# It spans multiple lines
print("Hello, World!")
```

---

## ⬜ Whitespace and Indentation

Python uses whitespace (spaces and tabs) to define the structure of the code. Indentation is crucial in Python, as it indicates blocks of code that belong together, such as the body of a function or a loop. We will cover functions and loops in later chapters, but here is a simple example to illustrate the concept of indentation.

```python
def greet(name):
    print(f"Hello, {name}!")  # Indented block

greet("Kingfisher") # Output: Hello, Kingfisher!
```

Incorrect indentation will lead to an `IndentationError`.

```python
def greet(name):
print(f"Hello, {name}!")  # This will raise an IndentationError

greet("Kingfisher")
```

### Ignored Whitespaces in Python

In Python, whitespaces around operators are ignored (though spacing is encouraged for readability). This means that the following lines of code are equivalent:

```python
x = 5 + 3
x=5+3
x = 5 +3
```

```python
x = 5 + 3  # Good practice
x=5+3      # Less readable
x = 5 +3   # Less readable
```

**Extra whitespaces inside data structures** (like dictionaries, lists, or tuples) are also ignored by the interpreter. This means you can add spaces or line breaks to improve readability without changing how the code runs.

For example, all of the following dictionary definitions are equivalent:

```python
my_dict = { "key1": "value1", "key2": "value2" }
my_dict = {"key1":        "value1",  "key2":"value2"}
my_dict = {
    "key1": "value1",
    "key2": "value2"
}
```

Python doesn't care about the spacing between keys, colons, and values — the meaning stays the same.

For best practices on code style, refer to the [PEP 8 - Style Guide for Python Code](https://peps.python.org/pep-0008/). PEP 8 is the de facto code style guide for Python, and it is widely adopted by the Python community.

:::{important} Inside strings, spaces are preserved literally!

The Python interpreter does not ignore spaces inside string literals. This means that the following two strings are different:

```python
s1 = "illinois rocks"
s2 = "illinois    rocks"
```

:::
