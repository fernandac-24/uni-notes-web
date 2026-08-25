Date: January 23, 2026

# Libraries 

## Modules

Is a libarry, that typically has one or more functions or other features built into it. 

## Import

give access to all the contents in the module 

"But we will always **refer** to the functions from that **module** by **using** 'random.' before the **function name**."

```python
import random
coin = random.choice(["head", "tail"])

print(coin)
```

## From

we import the specifc function, so is no longer neede to use the prefixus 

```python
from random import choice 
coin = choice(["head", "tail"])

print(coin)
```

## Random

![image.png](Lecture4/image.png)

### Function randint

random.radint(a,b)

select a number between a and b 

```python
from random import choice 
coin = choice(["head", "tail"])

print(coin)
```

### Function shuffle

random.shuffle(x)

recives an x and shuffle tem up, like cards. 

```python
import random 
cards = ["jack", "queen", "king" ]
random.shuffle(cards)
for card in cards:
    print(card)
    
## output (exemple)
jack
king
queen
```

## Statistics

![image.png](Lecture4/image%201.png)

### Function mean()

Calcula a média dos valores de uma sequência 

```python
import statistics

print (statistics.mean([100, 90]))

# output 
95
```

## Command-line arguments

allow you to provide arguments that is input to the program of just when you’re executing at the command line 

## Module sys

![image.png](Lecture4/image%202.png)

### Function argv

Whe can imidiatally run the file followed by the argument required by the function. 

```python
import sys
print("hello my name is", sys.argv[1]) 
## The posiytion 0 is the name of the file 

## No Terminal 
$ python3 Lecture4.py David
>>hello my name is David
```

### IntexError

Trying to access an  some element that does not exist in a list. 

It will  appear this error when the user try to run the function without providingtherequired argument. 

→ Solution 1 : 

```python
import sys
try:
    print("hello my name is", sys.argv[1])
except IndexError:
    print("Too few arguments")
```

→ Solucion 2:

```python
import sys
if len(sys.argv) < 2:
    print("Too few arguments")
elif len(sys.argv) >2:
    print("Too many arguments")
else: 
    print("hello my name is", sys.argv[1])

```

### Function exit

 **Encerramento Imediato:** Assim que é chamada, nenhuma linha de código abaixo dela será executada.

```python
## OPÇÃO 1
import sys
if len(sys.argv) < 2:
    sys.exit("Too few arguments")
elif len(sys.argv) >2:
    sys.exit("Too many arguments")

print("hello my name is", sys.argv[1])
```

```python
## OPÇÃO 2
import sys
if len(sys.argv) < 2:
    print("Too few arguments")
elif len(sys.argv) >2:
    print("Too many arguments")
 
print("hello my name is", sys.argv[1])
```

Na opção 2 temos um NameError, pois quando o utilizador não fornece argumentos suficientes (`len(sys.argv) < 2`), o teu programa imprime "Too few arguments", mas **continua a executar** as linhas de baixo.

Ou seja, tentará buscar depois na linha “ print("hello my name is", sys.argv[1])” o elemnto na posição 1, mesmo após ter verificado que ele não existe. 

Porém, na opção 1, a função exit impede que a função passe para a linha “print("hello my name is", sys.argv[1])” se uma das opções do if ou elix forem verificadas 

---

## Slices

Take a slice from a list, maybe from the beggining, or not 

similar to **String Slicing from lecture 2**

```python
import sys
if len(sys.argv) < 2:
    print("Too few arguments")

for arg in sys.argv[1:]: ###
    print("hello my name is", arg)
```

## Packages (Module)

Is a third-party libary that you can install on our own Mac or PC or our clound server and gain even more access 

![image.png](Lecture4/image%203.png)

## cowsay (package)

![image.png](Lecture4/image%204.png)

allows you to have a cow say something on your screen 

pip = allows you to install packages onto your PCs by just running a command. And voila, you have access to a whole new libary in Python

## APIs

is an application programming interface, and it can refer to Python files and functions, but ofthen, APIs really refer to third-party services that you and I can write code that talk to.

## request (package)

The requests libary allows you to make web request, internet request, using Python code essentially. 

![image.png](Lecture4/image%205.png)

copia e cola no navegador, e automaticamente faz o dowload 

→ [https://itunes.apple.com/search?entity=song&limit=1&term=weezer](https://itunes.apple.com/search?entity=song&limit=1&term=weezer)

it is the application programming interface for iTune 

The URL was manually constructed by reading the documentation for Apple’s API for ITune.  And what they told me is that if I want to search for information about songs in their database, I should specify entity equal song so that songs and not albums or artists or something like that 

So if we want information about one song, we have “limit=1” and if the band I want to search for, the artist is Weezer, I should specify term =weezer. 

**++** if we want information about 100 songs, we can just change limit = 1 to limit=100

And the tex file that was dowloaded follows a parttern

## JSON

Is a stardart text format know as JavaScript Object Notatio, wich is tipically used as a language agnostic format for exchanging data between computers. 

By language agnostic, I mean you don´t have to use JavaScript to read JSON, you can use any other language to rear it as well. 

→ And that’s an API, a mechanism whereby I can access data on someone else’s server and somehow integrate it into my own program.

```python
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])

print(response.json())
```

the output is JSOn, but Python convert it to a **dictionary** 

## JSON(libary)

![image.png](Lecture4/image%206.png)

Python also comes with a libary, called JSON, that allows you to manipulate JASON data and even just printy print it that is formatted in a way that’s going to be way easier for we to undertand. 

### Function dumps()

json.dumps(a, indent= x)

- **Transformação de Tipos:** Ela traduz os tipos de dados do Python para os seus equivalentes em JSON (por exemplo: um dicionário torna-se um objeto `{ }`, um valor `True` torna-se `true` em minúsculas, e `None` torna-se `null`).
- **Criação de Texto:** O resultado final não é mais uma coleção que o Python pode manipular diretamente, mas sim uma **string de texto**

### Fuction json()

Quando você executa **`response.json()`**, o resultado é um **objeto nativo do Python** (geralmente um **dicionário** ou uma **lista**).

Embora o método tenha "json" no nome, ele não retorna uma string JSON; ele faz o trabalho de **decodificar** o texto JSON que veio da internet e transformá-lo em algo que o Python entende diretamente.

---

```python
import requests
import sys
import json

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])

print(json.dumps(response.json()))
```

resultado sem o indent

![image.png](Lecture4/image%207.png)

### indent

```python
import requests
import sys
import json

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])

print(json.dumps(response.json(), indent= 2))
```

resultado com indent

![image.png](Lecture4/image%208.png)

O que o indent faz??

- **Human Readability:** By default, `json.dumps()` creates a compact, single-line string that is difficult for humans to read. Adding `indent` inserts **line breaks** and **leading spaces** to reflect the data's nested structure.
- **Spacing Count:** The number assigned to `indent` (in your case, **2**) tells Python exactly how many spaces to use at the beginning of each new line for every level of nesting.
    - `indent=2` uses two spaces per level.
    - `indent=4` is also a very common standard for even more whitespace.
- **Visualizing Structure:** It makes it immediately obvious which keys belong to which parent object, which is particularly helpful when debugging API responses.

## Working with API, requests, and JSON

Afther looking at the JSON from iTune, we can make an fuction that colects only, the name of the songs 

```python
import requests
import sys
import json

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=20&term=" + sys.argv[1])

o = response.jason()

for result in o["results"]:
    print(result["trackName"])
```

output will be 

$ python3 [itunes.py](http://itunes.py/) weezer
Say It Ain't So
Island In the Sun
Buddy Holly
Undone - The Sweater Song
Beverly Hills
Hash Pipe
Africa
Pork and Beans
Everybody Wants to Rule the World
Take on Me
My Name Is Jonas
I Just Threw out the Love of My Dreams
Mr. Blue Sky
In the Garage
Feels Like Summer
Perfect Situation
Billie Jean
All My Favorite Songs
No Scrubs
Happy Together

## Custom Libraries

if we created in an file called sayings a function called hello, and we want to import it to another file, we can use 

from sayings import hello

```python
from sayings import hello
```

but the output wouldn’t be the expeted, ‘cause the way we import it, go read the file sayings from top to bottom, and import the specifically the hello function. And when it reads, de file sayings, the function main is called 

so we have to add this line at the [saying.py](http://saying.py) 

```python
if __name__ == "__main__"
    main()
```

This is a special variable whose value is automatically set by Python to be , when you run a file from the command line  as running Python syings.py. 

so now, when we import a file, we’re not useing the command line so the final line that called the function main in the saying file won’t be called .

# Short - API

If I want to write a program to access the API for the Art Institute of Chicago

We can start by importing the Python module called requests 

That’s the site to look for the APIdocumentation for the Art Institute of Chicago

> [https://api.artic.edu/docs/#quick-start](https://api.artic.edu/docs/#quick-start)
> 

```python
import requests
import json

def main():
    try:
        response = requests.get("https://api.artic.edu/api/v1/artworks/search")
        response.raise_for_status()
    except requests.HTTPError:
        print("Couldn't complete request!")
        return
    
    content = response.json()
    for artwork in content["data"]: 
        print(f" * {artwork["title"]}")

main()
```

---

![image.png](Lecture4/image%209.png)

1. **Now we can actually search the collections of the Art Institute using**
2. their API and using this particular /artworks/search search route.

```python

import requests
import json

def main():
    try:
        response = requests.get(
            "https://api.artic.edu/api/v1/artworks/search",
            {"q": "Monet"}
            )
        response.raise_for_status()
    except requests.HTTPError:
        print("Couldn't complete request!")
        return
    
    content = response.json()
    for artwork in content["data"]: 
        print(f" * {artwork["title"]}")

main()
```

# Short - **Creating Modules and Packages**

A package is a colection of multiple modules. It can be created by making a folder and putting inside of it some especial file.

1. cria um nova pasta, que será o modulo 
2. Adiciona os ficheiros que faram parte do package 
3. Cria um novo ficehiro com o nome “__init__.py”

to import the package we can just :

```python
from modulename.specificfolder import functioname
```

# Short - Random

## Function choice()

random.choice()

Escolhe um elemento de uma lista 

## Function choices()

random.choices(l, weigths = l2, k =x)

onde l é a lista de onde os elementos serão retirados, e k será o nº de elementos que queresmo retirar da lista de uma única vez 

```python
import random

cards = ["jack" , "queen", "king"]

def main():
    print(random.choices(cards, k = 2))

main()
```

- But, for exemplo we could have as result [’queen’,’ queen’]
- Ou seja, a função choices não leva em conta o que foi selecionado anteriormente, podendo ter colo resultado o mesmo elemento da lista as k vezes.
    
    ---
    
    **What if I wanted to maybe weight the odds a little more in my favor** and make some things more likely to happen than others?
    
    → We can use the argument weigth, and as l2 we provide the list with the percentage of the propability that I want to to chose the elements from the list 
    
     + We just have to be sure that the total value of the list is 100
    

# Function sample()

random.sample(l, k= x)

Desempenha a mesma função da choices, porém não permite que como resultado apareça mais do que duas vezes o mesmo elemento. 

# Function seed

random.seed(x)

```python
import random

cards = ["jack" , "queen", "king"]

def main():
    random.seed(0)
    print(random.choices(cards , k = 2))

main()
```

initializes Python's **pseudo-random number generator (PRNG)** to make random results predictable and reproducible

Setting the seed here is a really good way **to help you debug your programs.**

Your programs can involve randomness, but you can actually be sure of the outcome when you set something like a random seed.

# Short- Style

Style, or the right type of style to use, is rather subjective, **and it depends typically on the programmer, on the company,** on the course, or on the language that you're actually using.

## PEP 8

And it happens to be such a proposal that standardized, or rather tried **to standardize, what our code should look like**

![image.png](Lecture4/image%2010.png)

### PycodeStyle

![image.png](Lecture4/image%2011.png)

![image.png](Lecture4/image%2012.png)

**It will actually take care of the process of reformatting** your code for you if it's a bit messy.

### Black

![image.png](Lecture4/image%2013.png)