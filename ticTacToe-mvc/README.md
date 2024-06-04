# ticTacToe

A simple tic tac toe app, to illustrate the use of MVC, MVP, and MVVM architectures to organize the application.

The master branch contains just the model - The brains & state of the tic tac toe game.

Other branches contain the model, plus a User Interface following:
* *mvc* - Is an example of using Model View Controller to model the UI / Model Interaction.
* *mvp* - Example of Model View Presenter
* *mvvm* - Example of Model View ViewModel with Databinding 


传统的mvc，activity当作c，数据类当作m，xml当作v。

代码结构上一般有controller目录和model目录，没有view目录，view由xml组成。

activity(即c)中持有m对象以及v对象（各种控件实例）。activity负责监听用户事件以及下层m回调，处理业务逻辑，改变v和m状态。

缺点，c太重太庞杂。有大量界面相关“细节”内容还要处理业务逻辑，难以维护，测试也不好做。

c同时操作了v和m。
Controller不仅负责操作Model进行业务逻辑处理，还负责进行View相关的界面展示处理，其中包括View的处理细节，
因此，我们可以说Controller肩负着过重的责任，只适用于小型的app，应用于大型app时，
会出现Massive View Controller（过重的视图控制器）的问题。

