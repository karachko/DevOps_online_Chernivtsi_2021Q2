# TASK1 #
- I wrote the code for the program **fizz_buzz**
- fizz_buzz.py
 
- 
```
def get_reply(number):
	if number%5==0 and number%3==0:
		return 'FizzBuzz'
	elif number%3==0:
		return 'Fizz'
	elif number%5==0:
		return 'Buzz'
	else:
		return '' 

```

- fizz_buzz_tests.py
-
```
import unittest
import fizz_buzz

class FizzBuzzTests(unittest.TestCase):

	def test_fizz(self):
		number=6
		
		result = fizz_buzz.get_reply(number)
		
		self.assertEqual(result, 'Fizz')
		
	def test_buzz(self):
		number=10
		
		result = fizz_buzz.get_reply(number)
		
		self.assertEqual(result, 'Buzz')
		
	def test_fizzbuzz(self):
		number=15
		result = fizz_buzz.get_reply(number)
		
		self.assertEqual(result, 'FizzBuzz')
		
if __name__ == '__main__':
	unittest.main()
```
- In the **PyCharm** in the terminal I run the command - python fizz_buzz_tests.py -v

-  (9.1.jpg) 
-  - ![9.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/tree/main/m9/task9.1/9.1.jpg)
