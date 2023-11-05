# HW2
```Swift
import SwiftUI

struct ContentView: View {
    @State var num:Int = 0 
    @State var hand:[String] = ["✌🏻","👊🏻","🖐🏻","🤌🏻","🖖🏻"]
    @State var word:[String] = ["剪刀","石頭","布","蜥蜴","史巴克"]
    //這是前陣子在網路上看到的新玩法，多了兩個元素，可以讓平局的機率變的很低。
    var body: some View{
        Text(hand[num])
            .font(.system(size:70))
            .frame(width:300,height:100,alignment: .center)
            .padding(.all,10)
            .foregroundColor(.white)
        
        Button(action:{
            num = Int.random(in: 0...4)
        },label:{
            Text("Go")
                .frame(width: 300, height: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                .font(.system(size: 70))
                .foregroundColor(.yellow)
                .fontWeight(.heavy)
                .background(Color .gray)
                .cornerRadius(20)
        })
        Text(word[num])
            .font(.system(size:50))
            .frame(width: 200, height: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
            .padding(.all,10)
            .foregroundColor(.red)
    }
}
```

<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/IMG_0028.jpeg">
