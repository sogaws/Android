# Android
2016-12-1 开始学习Android。
一、MVP : M-->model: 包含preferHelper、DatabaseHelpter、RetrofitService和AnotherHelpter.
                    为UI层提供的数据，或者保存UI层传下来的数据。 
                    Model 是用户界面需要显示数据的抽象，也可以理解为从业务数据（结果）那里到用户界面的抽象。 
                    Model 应该封装业务逻辑，不让Presenter和View知道业务逻辑层
         V-->view: 包含activity、fragment、viewgroup
                   View提供友好的交互、展示数据、响应用户操作，并都转发给Presenter来做具体的处理
         p-->presenter：逻辑控制层，分发逻辑。处理着程序各种逻辑的分发，收到View层UI上的反馈命令、定时命令、系统命令等指令后分发处理逻辑交由业务层                        做具体的业务操作，然后将得到的 Model 给 View 显示。
         在model层中抽象出一个DataManager，通过DataManager与数据的具体实现进行解耦，在p层我们只关心数据对象，不用关心数据是来自DB、SP还是网络。
         DataManger和具体的数据实现中还有一层Helper层进行DBHelper、SPHelper、RetrofirService等。
         
         Mvp中Presenter和View是相互交互的。Mvp拒绝View和Model直接交互，View和Model只能通过Presenter间接交互。因为Android对UI的操作必须在            UIThread上，而对Model的处理大多数是异步任务。通过转接一层可以很方便处理线程问题。Model和View是被动的，一切都由Presenter主导。
         一般把 Activity/Fragment 当做View，那么这时我们的Activity/Fragment中的代码简单多了，响应Presenter的指令对View进行操作，而这些操作是          在IVIEW 接口中定义好的。这样大部分代码转移到了Presenter中，而且一些业务代码被封装到了Model层去
