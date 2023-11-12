# somefile

1. UIViewController 控制器生命周期
	loadview加载view
viewDidload 加载控件和设置用户交互
viewwillapppeqr view即将显示
viewWillLayoutSubviews
viewDidLayoutSubviews
viewdidappeqr view显示完成、
view will disappear view即将消失，切换
viewdiddisqppear view消失，切换后
Deinit - 视图被销毁，此处需要对你在init和viewDidLoad中创建的对象进行释放
didReceiveMemoryWarning

2. KVC、KVO

只有set或者kvc可以实现
生成子类，通过重写父类的set方法 - 实现 _NSSetObjectValueAndNotify,其内部实现三步：
willChangeValueForKey
原来的set
didChangeValueForKey

class ViewController: UIViewController {     let per = Person()     override func viewDidLoad() {         super.viewDidLoad()         per.addObserver(self, forKeyPath: "name", options: [.new,.old], context: nil)     }      override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {         let num = Int(arc4random()%10000) + 1         per.setValue("\(num)", forKey: "name")     }      override func observeValue(forKeyPath keyPath: String?, of object: Any?, change: [NSKeyValueChangeKey : Any]?, context: UnsafeMutableRawPointer?) {         print(keyPath ?? "")         print("完成回调 -- \(String(describing: per.value(forKey: keyPath!)))")     }

3. Inout 本质：引用传递，copy in copy out
