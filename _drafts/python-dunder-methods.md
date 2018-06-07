---
layout: post
title: "Python dunder(magic) methods"
categories: python
---
A python object has many methods available at its disposal.
I wanted to list down all the possible dunder methods here for reference.

---
{% highlight python %}
In [15]: class Amount():
    ...:
    ...:     def __init__(self, amount=0):
    ...:         self._amount = amount

    ...:     @property
    ...:     def amount(self):
    ...:         return self._amount

    ...:     def __add__(self, other):
    ...:         if isinstance(other, Amount):
    ...:             return Amount(self.amount + other.amount)
    ...:         if isinstance(other, int):
    ...:             return Amount(self.amount + other)
    ...:         raise NotImplementedError
    ...:

In [16]: a = Amount(1)

In [17]: a.amount
Out[17]: 1

In [18]: a + 10
Out[18]: <__main__.Amount at 0x108ec59e8>

In [19]: foo = a + 10

In [20]: foo.amount
Out[20]: 11

In [21]: b = foo + a

In [22]: b
Out[22]: <__main__.Amount at 0x109480f98>

In [23]: b.amount
Out[23]: 12

In [24]: 4 + a
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-24-40053b62b981> in <module>()
----> 1 4 + a

TypeError: unsupported operand type(s) for +: 'int' and 'Amount'
{% endhighlight %}
