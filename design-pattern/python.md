# 装饰器模式
`python` 中通过装饰器语法实现装饰器模式

利用装饰器模式加速斐波那契数的计算

```python
import functools
import time


def memoize(fn):
    known = dict()

    @functools.wraps(fn)
    def memoizer(*args):
        if args not in known:
            known[args] = fn(*args)
        return known[args]
    return memoizer


@memoize
def fibonacci(n):
    assert (n >= 0), 'n must be >= 0'
    return n if n in {0, 1} else fibonacci(n-1) + fibonacci(n-2)


if __name__ == '__main__':
    ct = time.time()
    print(fibonacci(400))
    print(time.time() - ct)

```
# 适配器模式

```python
class Computer:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return 'the {} computer'.format(self.name)

    def execute(self):
        return 'execute a program'


class Synthesizer:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return 'the {} synthesizer'.format(self.name)

    def play(self):
        return 'is playing an electronic song'


class Human:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return '{} the human'.format(self.name)

    def speak(self):
        return 'syas hello'


class Adapter:
    def __init__(self, obj, adapted_methods):
        self.obj = obj
        self.__dict__.update(adapted_methods)

    def __str__(self):
        return str(self.obj)


def main():
    objects = [Computer('Asus')]
    synth = Synthesizer('moon')
    objects.append(Adapter(synth, dict(execute=synth.play)))
    human = Human('Bob')
    objects.append(Adapter(human, dict(execute=human.speak)))

    for i in objects:
        print('{} {}'.format(str(i), i.execute()))


if __name__ == '__main__':
    main()

# the Asus computer execute a program
# the moon synthesizer is playing an electronic song
# Bob the human syas hello
```