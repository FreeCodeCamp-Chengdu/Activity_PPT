### fizzBuzz.py:

```python
class Hiker:
    def __init__(self):
        self.arr = []
        for i in range(100):
            item = i+1
            tmpStr = ""
            if item%3 == 0:
                tmpStr = tmpStr + "Fizz"
            if item%5 == 0:
                tmpStr = tmpStr + "Buzz"
            if len(tmpStr) != 0:
                self.arr.append(tmpStr)
            else:
                self.arr.append(i+1)
    def getLength(self):
        return len(self.arr)
    def getArray(self, start, length):
        return self.arr[start-1:start-1+length]
```

### testFizzBuzz.py:

```python
import hiker
import unittest

class TestHiker(unittest.TestCase):
    def test_list_length(self):
        testHiker = hiker.Hiker()
        self.assertEqual(100, testHiker.getLength())
    def test_list(self):
        testHiker = hiker.Hiker()
        self.assertEqual([1,2,"Fizz",4], testHiker.getArray(1,4))
        self.assertEqual([2,"Fizz",4,"Buzz","Fizz",7], testHiker.getArray(2,6))
        self.assertEqual(["Fizz",13,14,"FizzBuzz"], testHiker.getArray(12,4))
if __name__ == '__main__':
    unittest.main()
```

