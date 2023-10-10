# **OOP**

**ООП(Объёктно-Ориентированное Программирование)** - ещё одна концепция                           
в разработке, где решение проблемы происходит через создание класса                              
и вызовов объекта этого класса. Объект всегда имеет свои                              
атрибуты и свои методы.


**Когда может применяться ООП:**


1) когда в решении можно выделить сущность класса;                                 
2) когда сложную логику в функциональности можно описать легко в ООП;                                            
3) в ООП существуют шаблоны, которыми можно описать сложную логику,                                      
благодаря чему не нужно ничего придумывать;                                   
4) повторное использование кода становится проще;                               
5) классы удобнее читать и использовать другим разработчикам;                                  
6) для того, чтобы изменить поведение во всех объектах, достаточно изменить                                
только класс, что позволяет быстро и надежно исправлять ошибки                                   
и поддерживать код.


### **OOP VS FUNCTIONS:**

---

**Различия ООП и функций**

|               | работа с классами                                                   | работа с функциями                                          |
|---------------|---------------------------------------------------------------------|-------------------------------------------------------------|
| определение   | Классы позволяют создавать объекты и описывать их свойства и методы | функции выполняют набор инструкций и возвращают значение    |
| состояние     | Объекты класса могут содержать состояние(переменные)                | Функции могут использовать аргументы и локальные переменные |
| использование | Методы класса вызываются на объектах этого класса                   | Функции вызываются с передачей аргументов                   |
| наследование  | Классы могут наследовать свойства и методы других классов           | Функции не могут наследовать свойства и методы              |

---

**Плюсы и минусы работы с классами**

| плюсы                                      | минусы                                              |
|--------------------------------------------|-----------------------------------------------------|
| Модульность и повторное использование кода | Большая сложность и уровень абстракции              |
| Инкапсуляция данных и поведения            | Увеличение объёма кода                              |
| Наследование и полиморфизм                 | Доп затраты на создание и поддержку класса          |
| Организация кода в логические блоки        | Возможность возникновения ошибок из-за наследования |

---

**Где применяется**

| Область применения                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------|
| Разработка больших и сложных программных систем, где необходимо организовать код в модули и логические блоки       |
| Создание объектно-ориентированных библиотек и фреймворков для повторного использования кода                        |
| Моделирование реальных объектов и систем, схожих с реальными объектами (например, моделирование бизнесс-процессов) |
| Создание пользовательских интерфейсов с использованием графических библиотек, таких как PyQt, или Tkinter          |
| Разработка игр и анимаций, где объекты и их поведение являются ключевыми элементами                                |

---

# **Классы и объекты:**

В **Python** почти всё, что вы используете является объектом какого-то                              
класса (даже типы данных в **Python** реализованы на **ООП**).                             


```python
a = 5

print(type(a))
print(type("asd"))
print(type([1, 2]))
```

**Классы** – это функции (**методы**) и переменные (**атрибуты**), которые описывают                                
определённую, независимую, понятную сущность (**объект**). Иными словами                                 
класс – это шаблон, которому подчиняется объект.                                        


**Из чего состоит класс?**

* **Инициализатор**
* **Статические** и **динамические** переменные
* **Методы**

```python
class MyTestClass:
    some_int = 7
    my_list = []
    is_false = True

    def __init__(self):
        self.some_int

    def f(self):
        pass

my_var = MyTestClass() # cube 1
my_var2 = MyTestClass() # cube 2
```

**Объект (экземпляр класса)** – это сущность, предмет или явление (**процесс**),                            
имеющий чётко выраженные границы, индивидуальность и поведение.                               
Создаётся на основе класса и выполняет инструкции, описанные в классе.                                      

**Объекты класса можно создавать в неограниченном количестве.**                                     

**Инициализатор** - место, где инициализируются динамические атрибуты класса                               

**Методы** - функции, только они находятся в классе и используются для объектов                         

**Основное отличие функций от методов в том, что методы в классах - динамические.**                                     


`self` – ключевое слово, которое является **ссылкой на объект** и используется                                    
для вызова методов и атрибутов определённого объекта в классе. Такая                                    
ссылка передаётся вместе со всеми аргументами, т.к. понимает, к                                  
какому объекту вы обращаетесь.                                     


```python
import random

class Cube:
    min_val = 1
    max_val = 6

    def roll(self): # self
        return random.randint(self.min_val, self.max_val)

cube = Cube()
cube.roll()
```

```python
class Dog:
  def __init__(self):
    print("woof!")

dog = Dog()
```

```python
class Cat:

  def __init__(self, pet_name):  # initializator
    self.cat_name = pet_name # Felix
    self.paws = 4
    self.ears = 2
    self.eyes = 2
    self.tail = True
    self.wool = True
    self.energy = 100
    self.sleep = False


  def say_mew(self):
    print(f"Your pet '{self.cat_name}' say 'Mew!'")


  def play(self, action):
    if self.energy >= 20:
            match action:
                case "play with hand":
                    self.energy -= 10
                    return f"The cat has been playing with your hand and is a little tired. {self.energy = }"
                case "play with a laser pointer":
                    self.energy -= 20
                    return f"The cat has been playing with a laser pointer and is a little tired. {self.energy = }"
                case "night madness":
                    return f"The cat's gone into 'night madness' mode. No energy wasted."
    else:
        return "The cat is tired, he's going to bed."
```

# **Свойства класса:**

`Свойства (атрибуты класса)` – это все переменные в классе, которые                            
могут использовать объекты                                  

`Статические свойства` – объявляются в классе и на протяжении всего                            
класса являются одинаковым значением                                  

`Динамические свойства` – задают начальное состояние определённому                              
объекту и меняются у каждого объекта при выполнении                             
какого-либо действия с ним                                 

Все динамические свойства инициализируется в методе `__init__` класса                                
и являются начальным состоянием объекта.                                  

---

**Методы класса:**

`Методы классов` - это функции, определенные внутри класса, которые                                
могут выполнять определенные операции с атрибутами (переменными)                                    
класса. Они предоставляют возможность обработки данных объектов                                  
класса и определения их поведения.                            


В **Python** существуют несколько типов методов классов:

1) **Методы экземпляра (instance methods):**
* Они принимают в качестве первого параметра ссылку на                            
экземпляр класса (`self`).                       
* Используются для работы с атрибутами экземпляра класса.                              
* Могут изменять состояние объекта, получать доступ к его                         
атрибутам и вызывать другие методы.                        
* Часто используются для реализации операций, специфичных                       
для каждого экземпляра класса.                                  

```python
class MyClass:
    def __init__(self, name):
        self.name = name

    def say_hello(self):
        print("Привет, меня зовут", self.name)

obj = MyClass("Антонина Зигизмундовна")
obj.say_hello()  # Привет, меня зовут Антонина Зигизмундовна
```

2) **Статические методы (static methods):**
* Они не принимают ссылку на экземпляр класса (`self`)                           
в качестве первого параметра.                                 
* Они могут выполняться без создания экземпляра класса.                                    
* Используются для выполнения операций, не зависящих от                              
состояния объекта или экземпляра класса.
* Могут быть полезными, когда нам нужно группировать операции,                                 
связанные с классом, внутри класса.                                 


```python
class MathUtils:
    @staticmethod
    def concatinate_numbers(x, y):
        return int(str(x) + str(y))

result = MathUtils.concatinate_numbers(5, 3)
print(result)
```

```python
class CurrencyConverter:
    exchange_rates = {
        'USD': 1.0,  # Базовая валюта
        'EUR': 0.85,  # Курс евро к доллару
        'GBP': 0.72,  # Курс фунта к доллару
        'JPY': 110.16  # Курс иены к доллару
    }

    @staticmethod
    def convert(amount, from_currency, to_currency):
        if from_currency != 'USD':
            amount = amount / CurrencyConverter.exchange_rates[from_currency]
        converted_amount = amount * CurrencyConverter.exchange_rates[to_currency]
        return converted_amount

usd_amount = 100.0
eur_amount = 100.0
amount = CurrencyConverter.convert(eur_amount, 'EUR', 'USD')
print(f"{usd_amount} EUR = {amount} USD")
```

3) **Методы класса (class methods):**
* Они принимают ссылку на класс (`cls`) в качестве первого параметра.                          
* Они имеют доступ к атрибутам класса, но не имеют доступа к                       
атрибутам экземпляров класса.                        
* Могут использоваться для выполнения операций, связанных с                         
классом в целом, а не с конкретным экземпляром класса.                               

```python
class CurrencyConverter:
    exchange_rates = {
        'USD': 1.0,  # Базовая валюта
        'EUR': 0.85,  # Курс евро к доллару
        'GBP': 0.72,  # Курс фунта к доллару
        'JPY': 110.16  # Курс иены к доллару
    }
    conversion_count = 0 # new

    @staticmethod
    def convert(amount, from_currency, to_currency):
        if from_currency != 'USD':
            amount = amount / CurrencyConverter.exchange_rates[from_currency]
        converted_amount = amount * CurrencyConverter.exchange_rates[to_currency]
        return converted_amount
    
    # new
    @classmethod
    def get_conversion_count(cls):
        return cls.conversion_count

usd_amount = 100.0
eur_amount = 100.0
amount = CurrencyConverter.convert(eur_amount, 'EUR', 'USD')
print(f"{usd_amount} EUR = {amount} USD")
```

в методе класса мы можем работать со статичными атрибутами.                               
Если нужно работать с динамичными атрибутами и методами - такое                                 
тоже возможно, но с дополнительными действиями:                                 

```python
class MyClass:
    def __init__(self, value):
        self.value = value

    def dynamic_method(self):
        return f"Dynamic method called with value: {self.value}"

    @classmethod
    def dynamic_class_method(cls, obj):
        return f"Value from dynamic_class_method: {obj.value}"

    @classmethod
    def call_dynamic_method(cls, obj):
        return obj.dynamic_method()

obj = MyClass(42)

result = MyClass.dynamic_class_method(obj)
print(result)

result = MyClass.call_dynamic_method(obj)
print(result)
```

**Методы** - поведение нашего объекта (то, как и что он может делать)                             

**Атрибуты** - состояние нашего объекта (то, какие изначально                                 
параметры у нашего объекта)                            


# **Модификаторы доступа:**

Модификаторы доступа в **Python** используются для определения уровня                                  
доступности атрибутов и методов внутри класса. Они указывают, какие                                
части кода могут получать доступ к определенным атрибутам или                             
методам класса. В **Python** есть три типа модификаторов доступа:                         
`public`, `protected` и `private`.                             


Модификаторы доступа применяются в классах для контроля доступа к их                            
членам. Они помогают управлять видимостью и использованием атрибутов                             
и методов класса извне класса и его подклассов.                               


* `Public`: Атрибуты и методы, к которым можно получить доступ из любого                           
места, не имеют специального префикса и являются публичными.                           

* `Protected`: Атрибуты и методы, которые должны быть доступны только внутри                              
класса и его подклассов, имеют префикс _ (одиночное подчеркивание).                              

* `Private`: Атрибуты и методы, которые должны быть доступны только внутри                              
самого класса, имеют префикс __ (двойное подчеркивание).                               


**Плюсы и минусы:**

**Плюсы:**

1) Модификаторы доступа обеспечивают **инкапсуляцию** и скрывают детали реализации                            
класса, предоставляя только необходимый интерфейс для работы с ним.                        
2) Они способствуют безопасности и предотвращают нежелательное изменение                           
или доступ к внутренним данным класса.                         
3) Модификаторы доступа способствуют поддержке и развитию кодовой базы,                             
так как они определяют контракт и интерфейс класса.                                   


**Минусы:**

1) Слишком строгое использование модификаторов доступа может усложнить                                
расширение и изменение класса, особенно в больших проектах.                                   
2) В **Python** нет жестких ограничений на модификаторы доступа, поэтому они                            
являются скорее соглашениями и не могут быть полностью принудительными.                                


```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Приватный атрибут

    def get_balance(self):
        return self.__balance

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
```

**Геттеры и сеттеры для работы с атрибутами:**                            

Для обеспечения доступа к приватным атрибутам класса могут использоваться геттеры                                  
и сеттеры. Геттеры используются для получения значения атрибута,                               
а сеттеры - для его изменения.                                   


```python
class Student:
    def __init__(self, name, age):
        self.__name = name
        self.__age = age

    def get_name(self):
        return self.__name

    def set_name(self, name):
        self.__name = name

    def get_age(self):
        return self.__age

    def set_age(self, age):
        if age >= 0:
            self.__age = age
```

**Инкапсуляция методов** позволяет ограничить доступ к определенным методам                               
класса, делая их "приватными". Это предотвращает прямой вызов                                  
таких методов извне класса.                                

```python
class Customer:
    def __init__(self, name):
        self.name = name

    def __validate(self, data):
        # Приватный метод, доступен только изнутри класса
        # Здесь можно выполнять проверки и валидации данных
        pass

    def create_order(self, order_data):
        self.__validate(order_data)
        # Дополнительная логика создания заказа
```

# **Классификация методов класса, генераторы и итераторы**

**Методы в ООП можно поделить на следующие фракции:**

* **Магические методы**
* **Динамические методы**
* **Статические методы**
* **Классовые методы**
* **Абстрактные методы**

```python
class Demo:
    counter = 0

    def __init__(self, name) -> None:
        self.name = name

    def dynamic_method(self):
        return f"Hello from dynamyc method! {self.name} ||| {self}"
```

**Магические методы:**

**Магические методы** - также известные как специальные методы в языке                             
**Python** представляют собой специальные функции, которые позволяют                            
определить поведение объектов класса при выполнении определенных                            
операций. Они начинаются и заканчиваются двойным подчеркиванием:                          
(`__init__`, `__str__`, `__len__`...)                                    


* `__init__(self)`: используется для инициализации объекта класса                      
и установки его атрибутов(если есть)                                

```python
class MyClass:
    def __init__(self, value):
        self.value = value

obj = MyClass(42)
```

* `__str__(self)`: возвращает строковое представление объекта                                   
класса, которое будет использовано при вызове функции str()                              

```python
class MyClass:
    def __str__(self):
        return "MyClass object"

obj = MyClass()
print(obj)  # Вывод: MyClass object
```

* `__repr__(self)`: определяет строковое представление объекта                            
при вызове функции repr().                            

```python
class MyClass:
    def __repr__(self):
        return "MyClass()"

obj = MyClass()
repr(obj)  # Вывод: 'MyClass()'
```

* `__len__(self):` Этот метод позволяет определить длину объекта, когда                       
он передается в функцию `len()`. Например, он может быть использован                         
для определения количества элементов в пользовательском контейнере.                            

```python
class MyList:
    def __init__(self, items):
        self.items = items

    def __len__(self):
        return len(self.items)

my_list = MyList([1, 2, 3])
print(len(my_list))
```

* `__getitem__(self, key):` Этот метод позволяет классам создавать                              
объекты, которые можно индексировать, как список или словарь.                            
Он вызывается при доступе к элементу по индексу,                           
например, `obj[key]`.                           

```python
class MyList:
    def __init__(self, items):
        self.items = items

    def __getitem__(self, index):
        return self.items[index]

my_list = MyList([1, 2, 3])
print(my_list[1])
```

* `__setitem__(self, key, value):` Этот метод используется для установки                            
значения элемента, когда объект индексируется, например,                           
`obj[key] = value`.                              

```python
class MyList:
    def __init__(self, items):
        self.items = items

    def __setitem__(self, index, value):
        self.items[index] = value

my_list = MyList([1, 2, 3])
my_list[1] = 42
print(my_list.items)
```

* `__delitem__(self, key):` Этот метод вызывается при удалении элемента                          
из объекта, который поддерживает индексирование, например, `del obj[key]`.                             

```python
class MyList:
    def __init__(self, items):
        self.items = items

    def __delitem__(self, index):
        del self.items[index]

my_list = MyList([1, 2, 3])
del my_list[1]
print(my_list.items)
```

* `__eq__(self, other):` Этот метод используется для определения,                               
равны ли два объекта. Он вызывается при использовании оператора `==`.                                

```python
class Point:
    def __init__(self, x):
        self.x = x

    def __eq__(self, other):
        return self.x == other.x

point1 = Point(1)
point2 = Point(1)
point3 = Point(3)

print(point1 == point2)
print(point1 == point3)
```

* `__lt__(self, other):` Этот метод используется для определения,                                  
меньше ли объект, чем другой объект. Он вызывается при использовании оператора `<`.                                

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __lt__(self, other):
        return self.age < other.age

student1 = Student("Alice", 20)
student2 = Student("Bob", 22)

print(student1 < student2)
```

* `__gt__(self, other):` Этот метод используется для определения, больше                              
ли объект, чем другой объект. Он вызывается при использовании оператора `>`.                             

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def __gt__(self, other):
        return self.title > other.title

book1 = Book("Python Basics", "John Smith")
book2 = Book("Advanced Python", "Alice Johnson")

print(book1 > book2)
```

* `__add__(self, other):` Этот метод используется для определения поведения                           
объекта при использовании оператора +. Например, он может быть                             
использован для сложения объектов.                                   

```python
class ComplexNumber:
    def __init__(self, real, imag):
        self.real = real
        self.imag = imag

    def __add__(self, other):
        real_sum = self.real + other.real
        imag_sum = self.imag + other.imag
        return ComplexNumber(real_sum, imag_sum)

num1 = ComplexNumber(1, 2)
num2 = ComplexNumber(3, 4)
result = num1 + num2

print(result.real, result.imag)
```

* `__sub__(self, other):` Этот метод используется для определения поведения                              
объекта при использовании оператора -. Например, он может быть                               
использован для вычитания объектов.                           

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __sub__(self, other):
        new_x = self.x - other.x
        new_y = self.y - other.y
        return Vector(new_x, new_y)

vector1 = Vector(3, 4)
vector2 = Vector(1, 2)
result = vector1 - vector2

print(result.x, result.y)
```

Так же существуют два таких интересных магических метода, как                          
`__enter__()` и `__exit__()`                           

Магические методы `__enter__()` и `__exit__()` связаны с контекстным                               
управлением (context management) в Python и используются для создания                             
и управления контекстами с помощью оператора `with`.                                

* `__enter__(self):` Этот метод вызывается при входе в блок кода `with`.                                  
Он выполняет предварительные настройки или ресурсные выделения, которые                                    
необходимы для контекста. `__enter__()` может возвращать какое-либо значение,                                
которое будет доступно в блоке `with` через ключевое слово `as`.                                    

* `__exit__(self, exc_type, exc_value, traceback):` Этот метод вызывается при                                   
выходе из блока кода `with`. Он обычно используется для выполнения завершающих                              
действий, таких как закрытие файлов, освобождение ресурсов и обработка                                
исключений. `exc_type`, `exc_value` и `traceback` представляют информацию об                                          
исключении, если оно произошло внутри блока `with`. Если исключение было                                    
подавлено, `exc_type`, `exc_value` и `traceback` будут None.                                     


```python
class FileContextManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()

# Использование контекстного менеджера
with FileContextManager("example.txt", "w") as file:
    file.write("Hello, World!")

# Файл будет автоматически закрыт при выходе из блока with
```

Преимущество использования магических методов `__enter__()` и `__exit__()`                                
заключается в том, что они позволяют автоматически управлять ресурсами и                              
обрабатывать исключения в контексте. Это делает код более чистым и безопасным,                          
особенно при работе с файлами, сетевыми соединениями, базами данных и другими                            
ресурсами, требующими явного освобождения или очистки.                              


```python
import sqlite3

class DatabaseConnection:
    def __init__(self, database):
        self.database = database
        self.connection = None

    def __enter__(self):
        self.connection = sqlite3.connect(self.database)
        return self.connection

    def __exit__(self, exc_type, exc_value, traceback):
        if self.connection:
            self.connection.close()

def create_table(connection):
    cursor = connection.cursor()
    cursor.execute('''CREATE TABLE IF NOT EXISTS employees (
                      id INTEGER PRIMARY KEY,
                      name TEXT,
                      position TEXT)''')

def insert_data(connection, data):
    cursor = connection.cursor()
    cursor.executemany("INSERT INTO employees (name, position) VALUES (?, ?)", data)
    connection.commit()

def display_data(connection):
    cursor = connection.cursor()
    cursor.execute("SELECT * FROM employees")
    result = cursor.fetchall()
    for row in result:
        print(row)

# Использование контекстного менеджера для работы с SQLite базой данных
db_filename = "mydb.sqlite"

with DatabaseConnection(db_filename) as conn:
    create_table(conn)
    data_to_insert = [("John Doe", "Manager"), ("Alice Johnson", "Engineer")]
    insert_data(conn, data_to_insert)
    display_data(conn)

# Соединение будет автоматически закрыто при выходе из блока with
```

Помимо этого есть ещё один интересный метод `__call__()`, который позволяет                        
нам писать использовать наши классы, как декораторы:                          

```python
import time

class TimingDecorator:
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        start_time = time.time()
        result = self.func(*args, **kwargs)
        end_time = time.time()
        print(f"Execution time: {end_time - start_time} seconds")
        return result

@TimingDecorator
def some_function():
    time.sleep(2)
    print("Function executed")

some_function()
```

```python
import time

class TimingDecorator:
    def __init__(self, message):
        self.message = message

    def __call__(self, func):
        def wrapper(*args, **kwargs):
            start_time = time.time()
            result = func(*args, **kwargs)
            end_time = time.time()
            print(f"{self.message}: {end_time - start_time} seconds")
            return result
        return wrapper

@TimingDecorator("Execution time")
def some_function():
    time.sleep(2)
    print("Function executed")

some_function()
```

с этими тремя методами можно даже написать такой класс, который в зависимости                               
от флага будет использоваться или как декоратор, или в контекстном менеджере:                              

```python
import time

class TimingDecorator:
    def __init__(self, message, use_as_manager=False):
        self.message = message
        self.use_as_manager = use_as_manager

    def __call__(self, func):
        def wrapper(*args, **kwargs):
            if not self.use_as_manager:
                start_time = time.time()
                result = func(*args, **kwargs)
                end_time = time.time()
                print(f"{self.message}: {end_time - start_time} seconds")
                return result
            else:
                with self:
                    return func(*args, **kwargs)

        return wrapper

    def __enter__(self):
        self.start_time = time.time()
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        end_time = time.time()
        print(f"{self.message}: {end_time - self.start_time} seconds")

# Использование как декоратора
@TimingDecorator("Execution time")
def some_function():
    time.sleep(2)
    print("Function executed")

some_function()

# Использование как контекстного менеджера
with TimingDecorator("Execution time", use_as_manager=True):
    time.sleep(2)
    print("Code executed in the context manager")
```

---

# **Задачи**

1) Переписать задачи работы с файлами с наших домашек, на классы.                                  

2) Реализовать небольшую систему входа:                                    
* вместо базы данных использовать csv файл                                 
* пользователь может создать аккаунт (name, email, password, repeat_password)                                    
* Реализовать создание аккаунта. проверить наличие такого пользователя                               
по email. Если есть - вывести сообщение, что такой пользователь                               
уже есть, аккаунт создать нельзя. Если нет - создать аккаунт,                                 
данные записать в csv файл.                              
* Реализация входа в систему. Проверять наличие пользователя по email.                          
Проверка пароля. Учесть все возможные расхождения, ошибки.                                

Все данные берутся и записываются из csv файла.                               
Пароль должен валидироваться. Это должен быть приватный метод.                             
Попробуйте реализовать чтение и запись при помощи контекстного метода и классов.                        