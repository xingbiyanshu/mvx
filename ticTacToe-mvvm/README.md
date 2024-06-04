# ticTacToe

A simple tic tac toe app, to illustrate the use of MVC, MVP, and MVVM architectures to organize the application.

The master branch contains just the model - The brains & state of the tic tac toe game.

Other branches contain the model, plus a User Interface following:
* *mvc* - Is an example of using Model View Controller to model the UI / Model Interaction.
* *mvp* - Example of Model View Presenter
* *mvvm* - Example of Model View ViewModel with Databinding 


m和mvc的一样；
v和mvp的一样；
vm是viewmodel。

代码结构model、view、viewmodel

关键点是使用了databinding，使得数据的变化可以同步更新到view的状态。

各view和model的绑定关系在xml里面定义好，包括onClick等事件回调。activity#oncreate设置xml文件和viewModel对象的绑定。

vm中的m对象都是包装成了ObservableField可观测的。

完成上述操作后对m的更改就会同步到v的状态了，反之亦然。

同样的view只负责通知vm界面事件

v和m不能直接通信，需要经过vm。

新的jet compose是mvvm模式的全新实现。


MVVM的核心思想：

进一步解耦：无论是MVC的Controller，还是MVP的Presenter，它们都会与View发生直接或者间接的依赖关系，通过Controller/Presenter来协调View和Model之间的交互，虽然MVP使用面向接口编程间接地将View与Model解耦，但并没有解决本质问题，而且还导致了接口数量和复杂度的增长。在MVVM中，ViewModel不会再持有View的引用，而是通过双向绑定机制来实现数据变化后的视图更新，它不再关心数据应该何时或者如何展示在视图上，一切都由双向绑定机制来完成，所以，MVVM在解耦程度上更进了一步。
基于观察者模式的数据驱动：数据驱动编程是编程范式中的一种，它关注数据的变化，从数据中引发其他组件的变化，是一种基于事件的编程，本质是观察者模式。数据驱动可以阻止数据与功能之间产生耦合，也可以在一定程度上提高开发效率。
双向绑定：双向绑定是数据驱动的一种很好的表现形式，即通过观察者模式，实现View的变化能实时反馈到数据上，数据的变化也可以实时反馈到View上。双向绑定是在单向绑定的基础上，对View增加了事件状态改变的监听，通过监听来动态修改数据。只有View有双向绑定，非View的部分一般只存在单向绑定。单向绑定在代码追踪和事件追踪上比双向绑定更加有优势，而双向绑定具有解耦良好、开发效率高等优势。

相较于前两者mvc/mvp，mvvm更复杂，小项目可能得不偿失。