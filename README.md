```python
# test_main.py
import unittest
from main import add  # 导入上面的代码

class TestMain(unittest.TestCase):

    # 测试用例1：测试正数相加
    def test_add_integers(self):
        result = add(1, 2)
        self.assertEqual(result, 3)  # 断言：结果应该是 3

    # 测试用例2：测试负数相加
    def test_add_negative(self):
        result = add(-1, -1)
        self.assertEqual(result, -2) # 断言：结果应该是 -2

if __name__ == '__main__':
    unittest.main()
