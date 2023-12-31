# **Повторение пройденного, практика**


**Типы данных**

* `int` - целые числа
* `float` - дробные числа
* `str` - строки
* `boolean` - логический тип (правда \ ложь)
* `list` - списки
* `tuple` - кортежи
* `set` - множества
* `frozenset` - неизменяемые множества
* `dict` - словари


**Простые типы данных:**

* `int`
* `float`
* `boolean`
* `NoneType`

**Коллекции:**

1) **последовательности**:
    * **неизменяемые**:
        * `str`
        * `tuple`
    * **изменяемые**:
        * `list`

2) **множества**:
    * **изменяемые**:
        * `set`
    * **неизменяемые**:
        * `frozenset`

3) **отображения**:
    * `dict`

---

**if - elif - else**

Конструкции, которые помогают вам выполнять тот, или иной блок кода,                   
в зависимости от условий, которые вы передаёте. Слишком много `if` не пилите                   
и старайтесь избегать сильной вложенности этих самых `if` конструкций - плохо                 
читается и считается не самым лучшим решением (макаронный код)

Так же в этой конструкции есть волшебное слово `raise`, которое позволяет нам                       
поднимать ошибки (которые мы передадим). В этом случае вы на выходе                    
получите **КАК РАЗ** ошибку, а не просто сообщение.


```python
# if - если (прописывается только один раз)
# elif - иначе если (может быть сколько угодно)
# else - иначе (может быть только один раз для блока)
# raise - подними
```

---

**Конструкции try-except**

Позволяют нам заранее **"предупреждать"** ошибки и как-то их обрабатывать.                        

Так же есть слово `else` - выполняется в случае, если ошибка **не была                 
отловлена** в блоке `try`.                      

Так же есть слово `pass` - позволяет нам ничего не делать в случае отлова                     
ошибки. Не очень гуд практика, так как вы просто **пропустите ошибку,                    
никак её не обработав**, что модет привести к таким себе событиям


---

**Циклы**

**Есть два основных вида циклов:**

1) `for` - для
2) `while` - пока


Наш `for` **работает быстрее**, так как он просто проходит по переданной                     
ему последовательности и что-то делает.

`While` же перед очередной итерацией **сперва проверяет валидность условия**.                   
Если условие ложное - **итерация не будет выполнена**, цикл закроется.                 

Так же у наших циклов есть такие слова, как:                      

`break` - выйди из цикла
`continue`- пропусти итерацию



---


```python
# Проверить входит ли символ\несколько символов в строку.
# Оба значения вводятся с клавиатуры
```

```python
# Пользователь вводит текущее время в часах (от 0 до 23). Напишите программу,                  
# которая выводит "Доброе утро", "Добрый день", "Добрый вечер" или               
# "Доброй ночи" в зависимости от введенного времени.
```

```python
# Пользователь вводит три числа. Напишите программу, которая определяет             
# максимальное из этих чисел и выводит его.
```

```python
# Пользователь вводит свой вес (в килограммах) и рост (в метрах).                       
# Напишите программу, которая вычисляет и выводит индекс массы тела (BMI)                   
# и дает рекомендации по весу (например, "недостаточная масса",                       
# "норма", "избыточная масса", "ожирение").
```

```python
# Пользователь вводит текст на английском. Напишите программу, которая подсчитывает                     
# и выводит количество гласных и согласных букв в тексте.

# гласные - ["a", "e", "i", "o", "u"]
```

```python
# Пользователь вводит целое число. Напишите программу, которая                
# определяет, является ли сумма его цифр четным числом, и                  
# выводит соответствующее сообщение.
```

```python
# С клавиатуры вводится предложение. Необходимо вывести эту строку,                   
# предварительно перевернув каждое слово в обратном порядке.
```

```python
# На вход подаётся какое-то целое число от 1 и выше.            
# Необходимо расчитать факториал этого числа.
```

```python
# Последовательность Фибоначчи На вход подаётся целое число от 1 и выше.                  
# Необходимо вывести число в последовательности, которое будет по порядку                  
# равное введённому числу. (Если ввели 5 - вывести пятое число в                
# последовательности. Ввели 22 - вывести 22-ое)
```

```python
# У вас есть дорогостоящая операция, которая принимает два значения и                
# выполняет вычисления. Напишите программу, которая кэширует результаты               
# этой операции, используя словарь, и возвращает результат, если вычисления                 
# для данных значений уже были выполнены. Если нет, выполните операцию,                 
# сохраните результат в словаре и верните его.
```




---

```python
# Написать калькулятор площади для разных фигур (круг\прямоугольник\треугольник)
```

```python
# Пользователь вводит ширину и высоту комнаты, а также ширину и высоту обоев             
# в рулоне. Напишите программу, которая определяет, сколько рулонов              
# обоев нужно для оклейки всей комнаты.
```

```python
# Пользователь вводит сумму кредита, процентную ставку и срок кредита                 
# в месяцах. Напишите программу, которая рассчитывает и выводит сумму              
# процентов, которые придется выплатить по кредиту.

# Сумма процентов = Сумма кредита * (Процентная ставка / 100) * (Срок кредита (в месяцах) / 12)
```

```python
# Пользователь вводит сумму вклада, процентную ставку и срок вклада в             
# годах. Напишите программу, которая рассчитывает и выводит итоговую сумму              
# вклада через указанный срок с учетом начисления процентов по простой ставке.
# добавить возможность выбора валюты. Для каждой валюты своя ставка
# Учесть текущую инфляцию и её рост в течение вашего срока вклада
```

```python
# В компании появился железяка-робот, который каждый день проезжает по офису                
# и считает количество программистов в офисе. Получить на ввод количество программистов              
# и вывести это количество в принте.Правильно подобрать окончания в зависимости от числа людей.
```