# head-first-design-patterns-Java
Head First设计模式 `Java` 版源码 



## 设计原则

1. 找出应用中可能需要变化之处，把它们独立出来，不要和那些不需要变化的代码混在一起。

2. 针对接口编程，而不是针对实现编程。

3. 多用组合，少用继承。

4. 为了交互对象之间的松耦合设计而努力。

5. 类应该对扩展开放，对修改关闭。

6. 最少知识原则：只和你的密友谈话。


   这是什么意思？当你正在设计一个系统，不管是任何对象，你都要注意它所交互的类有哪些，并注意它和这些类是如何交互的。

   这个原则希望我们在设计中，不要让太多的类耦合在一起，免得修改系统中一部分，会影响到其他部分。如果许多类之间相互依赖，那么这个系统就会变成一个易碎的系统，它需要花许多成本维护，也会因为太复杂而不容易被其他人了解。

7. 好莱坞原则：别调用我们，我们会调用你。

   好莱坞原则可以给我们一种防止“依赖腐败”的方法。当高层组件依赖底层组件，而底层组件又依赖高层组件，而高层组件又依赖边侧组件，而边侧组件又依赖底层组件时，依赖腐败就发生了。在这种情况下，没有人可以轻易地搞懂系统是如何设计的。

   在好莱坞原则之下，我们允许底层组件将自己挂钩到系统上，但是高层组件会决定什么时候和怎样使用这些底层组件。换句话说，高层组件对待底层组件的方式是“别调用我们，我们会调用你”。

8. 一个类应该只有一个引起变化的原因

   类的每个责任都有改变的潜在区域。超过一个责任，意味着超过一个改变的区域。

   这个原则告诉我们尽量让每个类保持单一责任。



## 设计模式



### 策略模式

定义了算法族，分别封装起来，让它们之间可以互相替换，此模式让算法的变化独立于使用算法的客户。

**要点：**

* 知道 OO 基础，并不足以让你设计出良好的 OO 系统。
* 良好的 OO 设计必须具备可复用、可扩充、可维护三个特性。
* 模式可以让我们建造出具有良好 OO 设计质量的系统。
* 模式被认为是历经验证的 OO 设计经验。
* 模式不是代码，而是针对设计问题的通用解决方案。你可把它们应用到特定的应用中。
* 模式不是被发明，而是被发现。
* 大多数的模式和原则，都着眼于软件变化的主题。
* 大多数的模式都允许系统局部改变独立于其他部分。
* 我们常把系统中会变化的部分抽出来封装。
* 模式让开发人员之间有共享的语言，能够最大化沟通的价值。



### 观察者模式

在对象之间定义一对多的依赖，这样一来，当一个对象改变状态，依赖它的对象都会收到通知，并自动更新。

**要点：**

* 观察者模式定义了对象之间一对多的关系
* 主题（也就是可观察者）用一个共同的接口来更新观察者
* 观察者和可观察者之间用松耦合方式结合，可观察者不知道观察者的细节，只知道观察者实现了观察者接口。
* 使用此模式时，你可从被观察者处推（push）或者（pull）拉数据（然而，推的方式被认为更正确）
* 有多个观察者时，不可以依赖特定的通知次序
* Java有多种观察者模式的实现，包括了通用的`java.util.Observable`
* 要注意`java.util.Observable`实现上所带来的一些问题
* 如果有必要的话，可以实现自己的`Observable`，这并不难，不要害怕
* Swing大量使用观察者模式，许多GUI框架也是如此
* 此模式也被应用在许多地方，例如：`JavaBeans`、`RMI`




### 装饰者模式

动态地将责任附加到对象上。想要扩展功能，装饰者提供有别于继承的另一种选择。

**要点：**

* 继承属于扩展形式之一，但不见得是达到弹性设计的最佳方式。
* 在我们的设计中，应该允许行为可以被扩展，而无须修改现有的代码。
* 组合和委托可用于在运行时动态地加上新的行为。
* 除了继承，装饰者模式也可以让我们扩展行为。
* 装饰者模式意味着一群装饰者类，这些类用来包装具体组件。
* 装饰者类反映出被装饰的组件类型（事实上，它们具有相同的类型，都经过接口或继承实现）。
* 装饰者可以在被装饰者的行为前面与/或后面加上自己的行为，甚至将被装饰者的行为整个取代掉，而达到特定的目的。
* 你可以用无数个装饰者包装一个组件。
* 装饰者一般对组件的客户是透明的，除非客户程序依赖于组件的具体类型。
* 装饰者会导致设计中出现许多小对象，如果过度使用，会让程序变得很复杂。



### 工厂方法模式

定义了一个创建对象的接口，但由子类决定要实例化的类是哪一个。工厂方法让类把实例化推迟到子类。



### 抽象工厂模式

提供一个接口，用于创建相关或依赖对象的家族，而不需要明确指定具体类。

**要点：**

* 所有的工厂都是用来封装对象的创建
* 简单工厂，虽然不是真正的设计模式，但仍不失为一个简单的方法，可以将客户程序从具体类解耦。
* 工厂方法使用继承：把对象的创建委托给子类，子类实现工厂方法来创建对象。
* 抽象工厂使用对象组合：对象的创建被实现在工厂接口所暴露出来的方法中。
* 所有工厂模式都通过减少应用程序和具体类之间的依赖促进松耦合。
* 工厂方法允许类将实例化延迟到子类进行。
* 抽象工厂创建相关的对象家族，而不需要依赖它们的具体类。
* 依赖倒置原则，指导我们免依赖具体类型，而要尽量依赖抽象。
* 工厂是很有威力的技巧，帮助我们针对抽象编程，而不要针对具体类编程。



### 单例模式

确保一个类只有一个实例，并提供一个全局访问点。

**要点：**

* 单例模式确保程序中一个类最多只有一个实例。
* 单例模式也提供访问这个实例的全局点。
* 在  JAVA 中实现单例模式需要私有的构造器，一个静态方法和静态变量。
* 确定在性能和资源上的限制，然后小心地选择适当的方案来实现单例，以解决多线程的问题（我们必须认定所有的程序都是多线程的）。
* 如果不是采用第五版的 JAVA 2，双重检查加锁实现会失效。
* 小心，你如果使用多个类加载器，可能导致单例失效而产生多个实例。
* 如果使用 JVM 1.2 或之前的版本，你必须建立单间注册表，以免垃圾收集器将单例收回。



### 命令模式

将“请求”封装成对象，以便使用不同的请求、队列或者日志来参数化其他对象。命令模式也支持可撤销的操作。（当需要将发出请求的对象和执行请求的对象解耦的时候，使用命令模式）

**要点：**

* 命令模式将发出请求的对象和执行请求的对象解耦。
* 在被解耦的两者之间是通过命令对象进行沟通的。命令对象封装了接收者和一个或一组动作。
* 调用者通过调用命令对象的 `execute()` 发出请求，这会使得接收者的动作被调用。
* 调用者可以接受命令当做参数，甚至在运行时动态地进行。
* 命令可以支持撤销，做法是实现一个 `undo()` 方法来回到 `execute()` 被执行前的状态。
* 宏命令是命令的一种简单的延伸，允许调用多个命令。宏方法也可以支持撤销。
* 实际操作时，很常见使用“聪明”命令对象，也就是直接实现了请求，而不是将工作委托给接收者。
* 命令也可以用来实现日志和事务系统。



### 适配器模式

将一个类的接口，转换成客户期望的另一个接口。适配器让原本接口不兼容的类可以合作无间。

**要点：**

* 当需要使用一个现有的类而其接口并不符合你的需要时，就使用适配器。
* 适配器改变接口以符合客户的期望。
* 实现一个适配器可能需要一番功夫，也可能不费功夫，视目标接口的大小与复杂度而定。
* 适配器模式有两种形式：对象适配器和类适配器。类适配器需要用到多重继承。



### 外观模式

提供了一个统一的接口，用来访问子系统中的一群接口。外观定义了一个高层接口，让子系统更容易使用。

**要点：**

* 当需要简化并统一一个很大的接口或者一群复杂的接口时，使用外观。
* 外观将客户从一个复杂的子系统中解耦。
* 实现一个外观，需要将子系统组合进外观中，然后将工作委托给子系统执行。
* 你可以为一个子系统实现一个以上的外观。
* 适配器将一个对象包装起来以改变气接口；装饰者将一个对象包装起来以增加新的行为和责任；而外观将一群对象“包装”起来以简化其接口。



### 模板方法模式

在一个方法中定义一个算法的骨架，而将一些步骤延迟到子类中。模板方法使得子类可以在不改变算法结构的情况下，重新定义算法中的某些步骤。

**要点：**

* “模板方法”定义了算法的步骤，把这些步骤的实现延迟到子类。
* 模板方法模式为我们提供了一种代码复用的重要技巧。
* 模板方法的抽象类可以定义具体方法、抽象方法和钩子。
* 抽象方法由子类实现。
* 钩子是一种方法，它在抽象类中不做事，或者只做默认的事情，子类可以选择要不要去覆盖它。
* 为了防止子类改变模板方法中的算法，可以将模板方法声明为 final。
* 好莱坞原则告诉我们，将决策权放到高层模块中，以便决定如何以及何时调用底层模块。
* 你将在真实世界代码中看到模板方法模式的许多变体，不要期待它们全都是一眼就可以被你认出的。
* 策略模式和模板方法模式都封装算法，一个用组合，一个用继承。
* 工厂方法是模板方法的一个特殊版本。



### 迭代器模式

提供一种方法顺序访问一个聚合对象的各个元素，而又不暴露其内部的表示。

**要点：**

* 迭代器允许访问聚合的元素，而不需要暴露它的内部结构。
* 迭代器将遍历聚合的工作封装进一个对象中。
* 当使用迭代器的时候，我们依赖聚合提供遍历。
* 迭代器提供了一个通用的接口，让我们遍历聚合的项，当我们编码使用聚合的项时，就可以使用多态机制。
* 我们应该努力让一个类只分配一个责任。



### 组合模式

允许你将对象组合成树形结构来表现“整体/部分”层次结构。组合能让客户以一致的方式处理个别对象以及对象组合。

**要点：**

* 组合模式提供一个结构，可同时包容个别对象和组合对象。
* 组合模式允许客户对个别对象以及组合对象一视同仁。
* 组合结构内的任意对象成为组件，组件可以是组合，也可以是叶节点。
* 在实现组合模式时，有许多设计上的折衷。你要根据需要平衡透明性和安全性。