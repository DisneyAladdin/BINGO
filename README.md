# BINGO
BINGO game for iPhone or iPad

シンプルで簡単なビンゴゲームアプリです．<br>
既に出た数字かどうかの検索機能付きです．<br>
直前に出た数字は， 小さく上の方に表示されます．

# Code
https://github.com/shutokawabata0723/BINGO/blob/master/simu/ViewController.swift

```swift
//
//  ViewController.swift
//  calculator
//
//  Created by 川畑修人 on 2018/01/29.
//  Copyright © 2018 川畑修人. All rights reserved.
//
import UIKit

class ViewController: UIViewController {
    
    @IBOutlet var button : UIButton!
    @IBOutlet var labelTest1 : UILabel!
    @IBOutlet var labelTest2 : UILabel!
    @IBOutlet var labelTest3 : UILabel!
    @IBOutlet var TextField  : UITextField!
    @IBOutlet var Small_Button : UIButton!
    var dataset = [0]
    var done    = [0]
    //var bingo_list = [0]
    var before = 0
    var count = 0
    var index_num = 0
    var bingo = 0
    var str = 0
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        //index_num = dataset.count
        dataset.remove(at: 0)
        //bingo_list.remove(at: 0)
        while count < 76 {
            count += 1
            dataset += [count]
        }
        print (dataset)
        
        labelTest1.text = "Let's BINGO!"
        labelTest2.text = ""
        //button.setTitle("PushMe" , for: .normal)
        //関数の宣言
        button.addTarget(self, action: #selector(self.buttonTapped(_:)), for: .touchUpInside)
        Small_Button.addTarget(self, action: #selector(self.smallButtonTapped(_sender:)), for: .touchUpInside)
    }
    
    
    @IBAction func buttonTapped(_ sender : Any) {
        
        labelTest1.text = String(before)
        let random = arc4random_uniform(UInt32(dataset.count))
        str = dataset[Int(random)]
        labelTest2.text = String(str)
        before = Int(str)
        done += [Int(str)]
        dataset.remove(at: Int(random))
        //print (dataset)
        print (done)
        if UInt32(dataset.count) == 0{
            labelTest2.text = ("END")
        }
    }
    
    @IBAction func smallButtonTapped(_sender : Any) {
        let text : String = TextField?.text ?? ""
        print(text)
        var counter = 0
        
        for var i in done {
            if String(i) == text{
                print ("Already")
                counter = 1
            }else{
                print ("yet")
            }
        }
        if counter == 1 {
            labelTest3.text = ("ALREADY")
        }else{
            labelTest3.text = ("YET")
        }
    }
    
    
    
    
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }    
}
```





# USAGE
 To start BINGO, push Button. 
 
 <img src="http://seoconsultant.sakura.ne.jp/shuto/data/fig/bingo-start.png" width="360px">
 
 The number just one before is shown with black color.<br>
 You can search number. Please enter the number to TextField and push "search" button.
 
 If the number has aready appeared, "ALREADY" appears.
 
 <img src="http://seoconsultant.sakura.ne.jp/shuto/data/fig/bingo-already.png" width="500px">

 Else, "YET" appears
 
 <img src="http://seoconsultant.sakura.ne.jp/shuto/data/fig/bingo-yet.png" width="500px">
 
# Licence
CopyRight (c) 2018 Shuto Kawabata

Released under the MIT licence

https://opensource.org/licenses/MIT

# Author
Shuto Kawabata
