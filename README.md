# python
python浅层次交流
多态, 不同的 子类对象调用 相同的 父类方法，产生 不同的 执行结果，可以增加代码的外部 调用灵活度，
多态以 继承 和 重写 父类方法 为前提
多态是调用方法的技巧，不会影响到类的内部设计
下面就用一段简单的代码来看看多态的优点

首先，我们看一下没有多态的代码：

class ArmyDog(object):

    def bite_enemy(self):
        print('追击敌人')

class DrugDog(object):

    def track_drug(self):
        print('追查毒品')


class Person(object):

    def work_with_army(self, dog):
        dog.bite_enemy()

    def work_with_drug(self, dog):
        dog.track_drug()


p = Person()
p.work_with_army(ArmyDog())
p.work_with_drug(DrugDog())
这样可以看出，如果添加一个类，继承Dog，代码的增加就很麻烦。
下面我们来看一下有多态的情形：

class Dog(object):
    def work(self):
        pass


class ArmyDog(Dog):
    def work(self):
        print('追击敌人')


class DrugDog(Dog):
    def work(self):
        print('追查毒品')


class Person(object):
    def work_with_dog(self, dog):  # 只要能接收父类对象，就能接收子类对象
        dog.work()  # 只要父类对象能工作，子类对象就能工作。并且不同子类会产生不同的执行效果。


p = Person()
p.work_with_dog(ArmyDog())
p.work_with_dog(DrugDog())

这样一来，添加一个类就显得很方便了。
