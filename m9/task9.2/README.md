# TASK2 #
- I wrote the code for the program **calculator**
- calc.py
 
- 
```
def sum(a, b):
    return a + b


def sub(a, b):
    return a - b


def mul(a, b):
    return a * b


def div(a, b):
    return a / b

```

- calculatortest.py
-
```
import unittest
import calc


class Test(unittest.TestCase):

    def test_sum(self):
        self.assertEqual(calc.sum(4, 7), 11)

    def test_sub(self):
        self.assertEqual(calc.sub(10, 5), 5)

    def test_mul(self):
        self.assertEqual(calc.mul(3, 7), 21)

    def test_div(self):
        self.assertEqual(calc.div(10, 2), 5)


if __name__ == '__main__':
    unittest.main()
```
- In the **PyCharm** in the terminal I ran the command - python calculatortest.py -v

-  (9.2.jpg) 
-  ![9.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m9/task9.2/9.2.jpg)

- I added the code to the calculatortest.py
- 
```
def test_sum1(self):
self.assertEqual(calc.sum(123456789123456789, 123456789123456789), 246913578246913578)
```
- In the **PyCharm** in the terminal I ran the command - python calculatortest.py -v

-  (9.3.jpg) 
-  ![9.3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m9/task9.2/9.3.jpg)

- I added the code to the calculatortest.py
- 
```
 def test_sum2(self):
 self.assertEqual(calc.sum(1, 'a'), 1)
```
- In the **PyCharm** in the terminal I ran the command - python calculatortest.py -v

-  (9.4.jpg) 
-  ![9.4.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m9/task9.2/9.4.jpg)

