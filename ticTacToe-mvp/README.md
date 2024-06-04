# ticTacToe

A simple tic tac toe app, to illustrate the use of MVC, MVP, and MVVM architectures to organize the application.

The master branch contains just the model - The brains & state of the tic tac toe game.

Other branches contain the model, plus a User Interface following:
* *mvc* - Is an example of using Model View Controller to model the UI / Model Interaction.
* *mvp* - Example of Model View Presenter
* *mvvm* - Example of Model View ViewModel with Databinding 


m对比mvc没变化；
v=activity+xml；
p是新增的控制类。最显著的特征是p和v之间通过接口交互。

代码结构上有model、view、presenter三个目录。

p持有m引用以及v接口引用；p监听m回调，告诉v该做什么，但具体怎么做由v去操作，p不涉及view的细节。
v告诉p界面事件，p去改变m状态（还可能需要通知v改变状态）。

随着业务需求增加，p和v的接口集会越来越庞大，p往往会变得臃肿。

MVP存在的问题：
Presenter责任过重：相比MVC，MVP模式中Presenter交出View的实现细节控制权，而只负责业务逻辑，但责任依然过重；
业务逻辑无法服用：传统MVP模式中，一个View对应一个Presenter，Presenter中业务逻辑只能为一个View服务，不能复用于多个模块之间，不同模块为了实现同样的业务逻辑，会多次重复操作导致大量冗余代码；
急剧扩增的接口数量：MVP采用面向接口编程，在进行业务迭代时，因发生变化而修改既有代码，往往需要连同修改接口层，而新增开放方法需要声明在接口中。

m<-> p <-> v
1. 各部分之间的通信，都是双向的。

2. View 与 Model 不发生联系，都通过 Presenter 传递。

3. View 非常薄，不部署任何业务逻辑，称为"被动视图"（Passive View），即没有任何主动性，而 Presenter非常厚，所有逻辑都部署在那里。