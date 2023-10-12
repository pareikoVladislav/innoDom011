# **Замыкание**

**Область видимости переменных**

Все переменные, которые мы объявляем в функции, включая её                              
аргументы, являются локальными, а это значит, что обратиться                                
к ним можно только внутри функции, за функцией они не существуют.

Глобальные переменные объявляются внутри функции и работают, а                               
также хранят значения полученные в функции за ней, учтите что                               
использовать такие переменные не всегда безопасно.

**Всего есть 4 области видимости переменных:**

`Build-in` - уровень сборки вашего питона                              
`Уровень файла` (глобальные переменные)                                
`Локальные переменные` (в блоке кода)                                 
`Замкнутые переменные` переменные, закрытые внутри функции                                       

---

## **Замыкание**

**Замыкание** - это функция, которая сохраняет доступ к переменным                       
из окружающей ее области видимости, даже после того, как эта                          
область видимости завершила свою работу.

Другими словами, **замыкание** - функция, которая имеет внутри себя другую,                       
вложенную функцию, и возвращает её. Вложенная функция имеет доступ к                     
атрибутам и переменным внешней функции.                


**Замыкания** (closures) в Python создаются путем **сохранения ссылки на переменные**                       
из внешней (родителя) функции внутри вложенной функции. Это позволяет                             
вложенной функции сохранить доступ к этим переменным **даже после завершения**                            
выполнения внешней функции. Этот механизм позволяет вам создавать функции,                          
которые "**запоминают**" значения переменных из окружающей области видимости.                        


```python
def outer_function(x):
   # outer func with `x` argument

   def inner_function(y):
      # inner function with `y` argument
      # this function has access to the local
      # environment of the external function
      return x * y
   return inner_function

closure = outer_function(10)
result = closure(5)
print(result)
```

Суть заключается в том, что Python сохраняет окружение (включая переменные)                           
внешней функции внутри замыкания, что позволяет замыканию обращаться к                           
этим переменным даже после завершения выполнения внешней функции. Этот                               
механизм очень полезен при создании функций, которые могут сохранять                             
состояние и контекст для последующих вызовов.                        

## **Примеры использования замыканий**

Замыкания можно использовать для создания счетчика функций, который будет                     
отслеживать, сколько раз функция была вызвана. За счёт этого вы можете                           
отследить количество вызовов ваших функций, что может помочь при                               
оптимизации кода.

В таком подходе может понадобиться дополнительное ключевое слово в питоне,                       
`nonlocal` для указания на то, что переменная не является локальной для                          
вложенной функции, а должна быть взята из ближайшей области видимости,                          
которая является областью видимости внешней функции.                                         

```python
def counter():
   # Внешняя функция, инициализирует счетчик
   count = 0

   def inner_function():
      # Вложенная функция, увеличивает счетчик и возвращает его значение
      nonlocal count # Объявляем count как nonlocal, чтобы изменять значение из вложенной функции
      count += 1
      return count

   return inner_function

my_counter = counter()

print(my_counter)
print(my_counter)
print(my_counter)
print(my_counter)
```

Когда мы вызываем **counter()**, она возвращает **inner_function()**, которая                          
замыкает (сохраняет) переменную count из внешней функции **counter()**. Таким                        
образом, каждый раз, когда мы вызываем **my_counter()**, мы работаем с той                         
же самой переменной count, которая сохраняется между вызовами функции.                          


замыкания могут быть переданы как аргументы в другие функции                         
или возвращены из них.                       

Замыкания и функции высшего порядка представляют мощную концепцию в языках                               
программирования, позволяя передавать функции как аргументы в другие функции                                
или возвращать их из функций. Это делает код более гибким и позволяет                            
работать с функциями как с данными.                                  

таким образом сторонние функции могут использовать замыкание или его внутреннюю                              
функцию для выполнения определенных операций. Это особенно полезно, когда                         
вы хотите передать логику выполнения функции как параметр.                             


```python
def apply(func, x):
    # Функция apply принимает функцию func и аргумент x
    return func(x)

def square(n):
    return n * n

def cube(n):
    return n * n * n

result1 = apply(square, 5)  # Передаем замыкание square
result2 = apply(cube, 5)    # Передаем замыкание cube

print(result1)  # Выведет 25
print(result2)  # Выведет 125
```

Функции могут также **возвращать замыкания** в качестве результата. Это позволяет                                    
создавать и возвращать функции на основе разных условий или параметров.                                  

```python
def multiplier(factor):
    # Функция multiplier принимает фактор и возвращает замыкание
    def multiply(x):
        return x * factor
    return multiply

double = multiplier(2)  # Возвращается замыкание с фактором 2
triple = multiplier(3)  # Возвращается замыкание с фактором 3

result1 = double(5)  # Умножение на 2
result2 = triple(5)  # Умножение на 3

print(result1)  # Выведет 10
print(result2)  # Выведет 15
```

## **Применение лямбда-функций в замыканиях**

**Лямбда-функции** также могут быть использованы внутри замыканий, что делает                            
замыкания более гибкими и позволяет создавать функции на месте с                   
помощью лямбда-функций.                          

```python
def generate_multiplier(factor):
    return lambda x: x * factor

double = generate_multiplier(2)  # Создаем лямбда-функцию, которая умножает на 2
triple = generate_multiplier(3)  # Создаем лямбда-функцию, которая умножает на 3

print(double(5))  # Выведет 10
print(triple(5))  # Выведет 15
```

`generate_multiplier` - это функция, которая возвращает лямбда-функцию.                              
**Лямбда-функция** умножает свой аргумент `x` на значение `factor`, которое                            
передается внутрь `generate_multiplier`. Это позволяет создавать разные                                 
функции на месте на основе разных значений `factor`.                                

Использование лямбда-функций в замыканиях может быть полезным, когда вам                              
**нужно динамически создавать функции с разной логикой** на основе                              
параметров или контекста.                               


## **Применение замыканий в реальной разработке**

Замыкания могут быть использованы **для обеспечения безопасности данных**                              
путем скрытия переменных и ограничения доступа к ним извне. Этот механизм                              
называется **инкапсуляцией** данных и представляет собой одну из основных                                 
концепций **объектно-ориентированного программирования**.                                  

В **Python**, однако, нет явной поддержки приватных переменных (которые                               
не могут быть доступны извне объекта), но мы можем использовать                            
замыкания для имитации этой функциональности.                                   


```python
def create_secure_account(balance, password):
    # Внешняя функция, скрывающая баланс и пароль

    def get_balance(pwd):
        # Вложенная функция, проверяющая пароль перед возвращением баланса
        if pwd == password:
            return balance
        else:
            return "Недопустимый пароль"

    def deposit(amount):
        # Вложенная функция для внесения средств
        nonlocal balance
        balance += amount
        return f"Внесено {amount}. Новый баланс: {balance}"

    def withdraw(amount):
        # Вложенная функция для снятия средств
        nonlocal balance
        if amount <= balance:
            balance -= amount
            return f"Снято {amount}. Новый баланс: {balance}"
        else:
            return "Недостаточно средств"

    return get_balance, deposit, withdraw

# Создаем безопасный счет
get_balance, deposit, withdraw = create_secure_account(1000, "password123")

# Попытка доступа к балансу с правильным паролем
print(get_balance("password123"))  # Выведет 1000

# Попытка доступа к балансу с неправильным паролем
print(get_balance("wrong_password"))  # Выведет "Недопустимый пароль"

# Внесение и снятие средств
print(deposit(500))  # Выведет "Внесено 500. Новый баланс: 1500"
print(withdraw(200))  # Выведет "Снято 200. Новый баланс: 1300"
print(withdraw(2000))  # Выведет "Недостаточно средств"
```

В этом примере переменные **balance** и **password** инкапсулированы внутри внешней                             
функции `create_secure_account`, и доступ к ним возможен только через                            
вложенные функции `get_balance`, `deposit` и `withdraw`, которые имеют доступ                           
к этим переменным благодаря замыканию. Таким образом, данные остаются                             
скрытыми и безопасными от прямого доступа извне, и доступ к ним                             
осуществляется только через управляемый интерфейс функций.                                        


**мемоизация через замыкания**

**Мемоизация** - это оптимизационная техника в программировании, которая                              
заключается в сохранении результатов выполнения функции для заданных входных                            
данных и последующем использовании сохраненных результатов при повторных                            
вызовах функции с теми же входными данными, вместо выполнения вычислений                            
заново. Это позволяет улучшить производительность функции, особенно в                            
случаях, когда функция вызывается с одними и теми же аргументами                              
несколько раз.                         

Замыкания играют важную роль в реализации мемоизации. С помощью замыканий                                
можно создать функцию-обертку, которая будет хранить результаты выполнения                           
функции и возвращать их, если входные данные уже были обработаны.                               


**Задания**

1) Написать функцию, которая возвращает замыкание для                           
вычисления факториала.                      

2) Создать функцию для генерации случайных паролей                         
с заданной длиной, используя замыкания.

---

# **Рекурсии**

![img_21.png](img_21.png)

---

**Рекурсия** – это подход в программировании, при котором функция вызывает                           
сама себя. Любую рекурсивную функцию можно представить как цикл, а                         
цикл можно представить как рекурсию.

**Преимущества рекурсии:**

1) каждый новый вызов функции в функции начинается с чистого листа,                            
   а значения из предыдущих вызовов отдаются в стек.
2) код, написанный через рекурсию читается проще. Решения выглядит лучше.

**Недостатки рекурсии:**

1) размер стека, которому проталкиваются элементы из каждого                        
   вызова не безграничен.
2) рекурсию трудно представить, если рекурсия спроектирована плохо,                         
   она может убить ваше приложение или сильно его замедлить.

**Правила создания рекурсий:**

1) рекурсия не должна создавать больше чем 3000 слоев (вызовов)
2) у рекурсии всегда должно быть условие остановки
3) использовать рекурсию, для того чтобы решение становилось меньше и понятнее
4) использовать рекурсию, когда знаешь глубину вызов
5) если код читает другой человек, выбор в пользу рекурсии                         
   (код красивее и понятнее)
6) если скорость не так важна выбор в пользу рекурсии

```python
# пример рекурсии

def greeting(value: int) -> None:
    if value == 0:
        return 0
    print(f"Hello! This is recursion! {value}")
    greeting(value - 1)
```

**Основные принципы рекурсивных функций:**

`Базовый случай:` Рекурсивная функция всегда должна иметь **"базовый случай"**                            
или **"условие выхода"**, которое определяет, когда рекурсия должна завершиться.                      
Этот базовый случай обычно определяется так, чтобы функция не                         
вызывала себя бесконечно.                        

`Рекурсивный случай:` Это шаг, при котором функция вызывает саму себя с                         
аргументами, которые приближают к базовому случаю. Это позволяет функции                           
продолжать выполнение до тех пор, пока не будет достигнут базовый                           
случай и рекурсия завершится.                            


**Рекурсия** - мощный инструмент в программировании, но её следует                          
использовать осторожно, чтобы избежать бесконечных циклов и                             
излишних накладных расходов на память.                      


**Особенности рекурсивных функций в Python**

**Максимальная глубина рекурсии:**

В **Python** есть ограничение на максимальную глубину рекурсии, которое                          
определяется максимальным количеством вызовов функции, которые могут быть                         
вложены друг в друга. Это ограничение называется "**максимальной глубиной                            
стека**" (**maximum recursion depth**).                          

Значение максимальной глубины рекурсии зависит от конкретной версии                           
**Python** и его настроек. В стандартной настройке **Python** это значение                            
обычно составляет `1000` вызовов функций.
При превышении максимальной глубины рекурсии **Python** вызовет                         
исключение `RecursionError`.                                  

```python
def infinity_recursion(a):
   return infinity_recursion(a + 1)
```

В **Python** можно переопределить максимальное количество вызовов рекурсии,                           
изменяя глубину стека с помощью функции `sys.setrecursionlimit()`. Однако                         
это не рекомендуется делать без веских причин, так как увеличение глубины                          
стека может привести к переполнению стека и ошибкам в работе программы.                            
Кроме того, стандартное значение глубины стека установлено на определенное                       
значение для обеспечения безопасности выполнения программ.                            

```python
import sys

new_limit = 500  # Новое значение глубины стека
sys.setrecursionlimit(new_limit)

# Теперь можно выполнять более глубокие рекурсивные вызовы
```

Вызов рекурсии может находиться не только в конце функции, но и в любом месте                         
функции, в зависимости от логики задачи. Передача управления рекурсивному                          
вызову в середине функции вполне допустима, и это может быть полезным                           
в некоторых сценариях.                          

```python
def countdown(n):
    print(n)
    if n > 0:
        countdown(n - 1)
    print("Выполнено для", n)

countdown(5)
```

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        result = factorial(n - 1)
        return n * result

result = factorial(5)
print("Факториал равен:", result)
```


**Оптимизация хвостовой рекурсии:**

**Хвостовая рекурсия** (**tail recursion**) - это специальный                         
вид рекурсии, когда рекурсивный вызов является последней операцией                        
в функции перед возвратом значения.                              

**Python** не поддерживает оптимизацию хвостовой рекурсии "**из коробки**"                         
(по умолчанию). Это означает, что при использовании хвостовой рекурсии                                 
**Python** будет по-прежнему создавать новые фреймы стека для каждого                               
рекурсивного вызова, что может привести к превышению максимальной                          
глубины рекурсии.                             

Оптимизацию хвостовой рекурсии можно достичь с помощью различных техник,                             
таких как использование циклов вместо рекурсии или использование специальных                         
библиотек, таких как `functools.lru_cache`, которые предоставляют мемоизацию                            
(кэширование) результата функции для избежания повторных вычислений.                               

```python
import functools

@functools.lru_cache(maxsize=None)
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

```

**Задачи**

1) Написать рекурсию на вычисление факториала введённого числа                                

2) Написать рекурсию на вычисление числа фибоначчи              

3) Написать рекурсию на вычисление суммы элементов списка


---

# **Домашка**

1) Написать калькулятор с использованием замыканий.                       
Калькулятор должен включать в себя все базовые математические                          
операции, а так же квадратный корень и кубический корень чисел                            

































































































