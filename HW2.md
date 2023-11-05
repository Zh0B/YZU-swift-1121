# HW2

這是特別版的剪刀石頭布，有五種拳可以選擇，使平局機率降至非常低。
```Swift
import SwiftUI

struct ContentView: View {
    @State var num: Int = 0
    @State var myNum: Int = 0
    @State var hand: [String] = ["❓","✌🏻", "👊🏻", "🖐🏻", "🤌🏻", "🖖🏻"]
    @State var word: [String] = ["❓","剪刀", "石頭", "布", "蜥蜴", "史巴克"]
    @State var result:String = ""
    
    var body: some View {
        ZStack {
            LinearGradient(gradient: Gradient(colors: [Color.blue, Color.purple]), startPoint: .top, endPoint: .bottom) //漸層背景
                .edgesIgnoringSafeArea(.all)
            
            VStack {
                Text(hand[num])
                    .font(.system(size: 70))
                    .frame(width: 300, height: 100, alignment: .center)
                    .padding(.all, 10)
                    
                Button(action: {
                    num = Int.random(in: 1...5)
                    determine()
                    
                }, label: {
                    Text("Play")
                        .frame(width: 300, height: 100, alignment: .center)
                        .font(.system(size: 70))
                        .foregroundColor(.yellow)
                        .fontWeight(.heavy)
                        .background(Color.gray)
                        .cornerRadius(20)
                })
                
                HStack{
                    Button(action:{
                        myNum -= 1 
                        if(myNum <= 0){
                            myNum = 5
                        }
                    },label:{
                        Text("⬅️")
                            .font(.system(size:50))
                    })
                    Text(hand[myNum])
                        .font(.system(size: 70))
                        .frame(width: 100, height: 100, alignment: .center)
                        .padding(.all, 10)
                    Button(action:{
                        if(myNum < 5){
                            myNum += 1
                        }else{
                            myNum = 1
                        }
                    },label:{
                        Text("➡️")
                            .font(.system(size:50))
                    })
                }
                Text("按下左右來選擇要出的拳！")
                    .font(.system(size:30))
                    .foregroundColor(.yellow)
                    .frame(height: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/)
                Text(result)
                    .font(.system(size: 50))
                    .foregroundColor(.red)
            }
        }
    }
    func determine(){
        if(myNum == 0){
            result = "你沒出拳..."
        }else if(num == myNum){
            result = "Tie"
        }else if(num == 1 && myNum == 3) || (num == 1 && myNum == 4) || 
                (num == 2 && myNum == 1) || (num == 2 && myNum == 4) || 
                (num == 3 && myNum == 2) || (num == 3 && myNum == 5) ||
                (num == 4 && myNum == 3) || (num == 4 && myNum == 5) || 
                (num == 5 && myNum == 1) || (num == 5 && myNum == 2){
            result = "You Lose ！"
        }else{
            result = "You Win 🎉"
        }
    }
}
```

<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/HW2_ready_img.jpg">
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/HW2_win_img.jpg">
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/HW2_lose_img.jpg">
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/HW2_tie_img.jpg">
