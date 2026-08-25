# Object-Oriented Programming

Date: January 25, 2026


## Tuples

```python
def main():
    student = get_student()
    print(f"{student[0]} from {student[1]}")

def get_student():
    name =  input("Name: ")
    house = input("House: ")
    return (name, house)
```

But tuples are imutable 

## Classes and Objects

### Classes

Allows you to create your own data types, and give them names.

![image.png](Lecture8/image.png)

```python
##Criando uma class
class Students:
    ...

def main():
    student = get_student()
    #student.name -> acessa o nome atribuido ao student
    print(f"{student.name} from {student.house}")

def get_student():
		#student is an object of the class Students
    student = Students()
    #sitaxe usada para atribuir um nome ao student
    student.name= input("Name: ")
    student.house = input("House: ")
    return student

if __name__ == "__main__":
    main()
```

### Objects

Everytime you use a class you are creating an object. 

So is technically instatian of. And another term for objects would actually be an instance. 

## Instance Methods

### Methods

Some functions that you can define inside a class, and they just behave in a specil way by nature of how Python works.

They allow you to determine behavior in a standard way. 

```python
class Students:
    def __init__(self):
```

### init method

if you want to initialize the contents of an object from a class you define this method. 

```python
class Students:
    def __init__(self, name, house):
        self.name = name
        self.house = house
```

This is installing into the otherwise empty object the value name and house, and storing them in. really, identically named instace variables in the object. 

```python
class Students:
    def __init__(self, name, house):
        self.name = name
        self.house = house

def main():
    student = get_student()
    #student.name -> acessa o nome atribuido ao student
    print(f"{student.name} from {student.house}")

def get_student():
    name = input("Name: ")
    house = ("House: ")
    student = Students(name, house)
    return student

if __name__ == "__main__":
    main()
```

### not name

verifica se name == “”

### raise (keyword)

```python
class Students:
    def __init__(self, name, house):
        if not name:
            raise ValueError("Missing name")
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self.name = name
        self.house = house
```

## Validating Attributes

### “__str__” method

This is a secial method that if you define it inside of you class Python will just automatically call this function for you any time some other function wants to see your object as a string. 

```python
    def __str__(self):
        return f"{self.name} from {self.house}"
        
```

---

## The String Method

```python
class Student:
    def __init__(self, name, house):
        if not name:
            raise ValueError("Missing name")
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"

def main():
    student = get_student()
    #student.name -> acessa o nome atribuido ao student
    print(student)

def get_student():
    name = input("Name: ")
    house = input("House: ")
    return Student(name, house)

if __name__ == "__main__":
    main()
```

## Custom Methods

```python
class Student:
    def __init__(self, name, house, patronus):
        if not name:
            raise ValueError("Missing name")
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self.name = name
        self.house = house
        self.patronus = patronus

    def __str__(self):
        return f"{self.name} from {self.house}"
    
    def charm(self):
        match self.patronus:
            case "Stang":
                return "🐴"
            case "Otter":
                return "🦦 "
            case "Jack Russall terrier":
                return "🐶"
            case _ :
                return "/"

def main():
    student = get_student()
    #student.name -> acessa o nome atribuido ao student
    print("Expecto Patronum!")
    print(student.charm())

def get_student():
    name = input("Name: ")
    house = input("House: ")
    patronus = input("Patronus: ")
    return Student(name, house, patronus)

if __name__ == "__main__":
    main()
```

## Properties, Getters and Setters

```python
class Student:
    def __init__(self, name, house):
        if not name:
            raise ValueError("Missing name")
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"

def main():
    student = get_student()
    student.house = "Number Four, Pivet Drive"
    print(student)

def get_student():
    name = input("Name: ")
    house = input("House: ")
    return Student(name, house)

if __name__ == "__main__":
    main()
```

Na linha *student.house = "Number Four, Pivet Drive"*   Atribuimos um novo valor para house, ou seja, diferente de um Tuplo, os valores de um objeto de uma classe podem ser alterados.    

### Properties

Is an attribute that has even more defense mechanism put into place a little more functionality implemented by you, to prevent programmers for messing things up like attributes.

The way to prevente that a value is atrtibute to an object, is requiring that in order to access an attribute you go through some function. And let´s require that, in order to set some attribute you go through some function 

→ Conventionally, those functions are called a getter function and a setter function

```python
class Student:
    def __init__(self, name, house):
        if not name:
            raise ValueError("Missing name")
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"
    
    #Getter
    @property
    def house(self):
        return self._home 
    
    #Setter
    @house.setter
    def house(self, house):
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self._house = house

```

+The underscore before house, is to indentify when i reffer the functionhouse, or the variable. 

```python
class Student:
    def __init__(self, name, house):
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"
    
    @property
    def name(self):
        return self.__name 
    
    @name.setter
    def name(self, name):
        if not name:
            raise ValueError("Missing name")
        self._name = name

    #Getter
    @property
    def house(self):
        return self._home 
    
    #Setter
    @house.setter
    def house(self, house):
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self._house = house

def main():
    student = get_student()
    print(student)

def get_student():
    name = input("Name: ")
    house = input("House: ")
    return Student(name, house)

if __name__ == "__main__":
    main()
```

Int é uma class e srt também 

## Types and Classes

```python
print(type(50))
```

O output é o data type do que está dentro, ou seja, neste caso temos: 

<class 'int'>

## Class Methods

```python
@classmethod
```

function that you can use to specify that this method is not by default, implicity an instance method that has access to self, the objectt itself. This is a class method that´s not going to have access to self, but it does know what class it´s inside. 

```python
import random

class Hat:
    def __init__(self):
        self.houses = ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]

    def sort(self, name):
        print(name, "is in", random.choice(self.houses))

hat = Hat()
hat.sort("Harry")
```

### Usando classmethod

```python
import random

class Hat:
    houses = ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]
    
    @classmethod
    def sort(cls, name):
        print(name, "is in", random.choice(cls.houses))

Hat.sort("Harry")
```

now we are creating a variable associated with the class. 

### Doing the [student.py](http://student.py) com classmethod

replacing the function get_student for the @classmethod get 

So, now we have everything related to the class Student inside of the class. 

```python
class Student:
    def __init__(self, name, house):
        self.name = name
        self.house = house

    def __str__(self):
        return f"{self.name} from {self.house}"
    
    @classmethod
    def get(cls):
        name = input("Name: ")
        house = input("House: ")
        return cls(name, house)
    
    @property
    def name(self):
        return self.__name 
    
    @name.setter
    def name(self, name):
        if not name:
            raise ValueError("Missing name")
        self._name = name

    #Getter
    @property
    def house(self):
        return self._home 
    
    #Setter
    @house.setter
    def house(self, house):
        if house not in ["Gryffindor", "Hufflepuff", "Ravenclaw", "Slytherin"]:
            raise ValueError("Invalid house")
        self._house = house

def main():
    student = Student.get()
    print(student)
  

if __name__ == "__main__":
    main()
```

## Inheritance

```python
#Superclass
class Wizard :
    def __init__(self, name):
        if not name:
            raise ValueError("Missing name")
        self.name = name

class Student(Wizard):
    def __init__(self, name, house):
        #Utilizando a função init da super class
        super().__init__(name)
        self.house = house

class Professor(Wizard):
    def __init__(self, name, subject):
        super().__init__(name)
        self.subject = subject

wizard = Wizard("Albus")
student = Student("Harry", "Gryffindor")
professor = Professor ("Severus", "Defense Against the Darck Arts")
```

### Base Exception

![image.png](Lecture8/image%201.png)

## Operator Overloading

### method “add”

object.__add__(self, other)

![image.png](Lecture8/image%202.png)

# Resumo Python PDF
> [!tldr]- Click here to view PDF
> ![[python_resumo_em_tabelas.pdf]]