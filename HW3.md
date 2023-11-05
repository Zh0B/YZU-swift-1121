# HW3
```swift
import SwiftUI
struct TitleView: View{
    var body: some View{
        VStack(alignment:.center,spacing:2){
            Text("我的奇怪動物園")
                .frame(maxWidth:.infinity)
                .font(.system(size:30))
                .foregroundColor(Color(red: 20/255,
                   green: 100/255,blue: 135/255))
            Text("進場請先買票")
                .font(/*@START_MENU_TOKEN@*/.title/*@END_MENU_TOKEN@*/)
                .foregroundColor(Color(red:199/255,
                   green: 40/255,blue:16/255))
        }.background(Color.brown)
        .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
    }
}

struct ContentView: View{
    var body: some View{
        VStack{
            TitleView()
            ZStack{
                ticketView()
                Text("售票員")
                    .foregroundColor(.orange)
                    .font(.system(size:30))
                    .padding(.all,5)
                    .background(Color.gray)
                    .opacity(0.5)
                    .offset(x:30,y:30)
            }
            
            HStack{
                DogView(imageName: "Ghost",name: "萬聖鬼鬼")
                DogView(imageName: "Haski",name: "嘿嘿墨鏡")
                DogView(imageName: "Shiba",name: "紳士")
            }
            HStack{
                catView(imageName: "Big",name: "有這麼大")
                catView(imageName: "Smile",name: "想色色")
                catView(imageName: "Lip", name: "殼以嗎")
            }
            ZStack{
                managerView()
                Text("他是管理員")
                    .font(.system(size:30))
                    .foregroundColor(.black)
                    .padding(.all,5)
                    .background(Color.green)
                    .opacity(0.5)
                    .offset(x:70,y:35)
            }
        }.background(Color.brown)
        .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
    }
}

struct ticketView: View{
    var body:some View{
        VStack{
            Image("Raccoon")
                .resizable()
                .aspectRatio(contentMode:.fit)
            Text("是浣熊哦")
                .fontWeight(/*@START_MENU_TOKEN@*/.bold/*@END_MENU_TOKEN@*/)
                .font(.system(size:30))
        }
        .background(Color.brown)
        .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
    }
}

struct DogView: View{
    var imageName:String
    var name:String
    var body:some View{
        VStack{
            Image(imageName)
            .resizable()
            .aspectRatio(contentMode:.fill)
            .frame(height: 100, alignment:.bottom)
            Text(name)
            .fontWeight(.bold).font(.system(size: 25))
            
        }
        .frame(minWidth: 0, idealWidth: 100,
               maxWidth: .infinity, minHeight: 0,
               idealHeight: 100, maxHeight: .infinity, alignment: .center)
        .background(Color.brown)
        .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
    }
    
}
struct catView: View{
    var imageName:String
    var name:String
    var body:some View{
        VStack{
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode:.fill)
                .frame(height: 100, alignment:.bottom)
            Text(name)
                .fontWeight(.bold).font(.system(size: 25))
            
        }
        .frame(minWidth: 0, idealWidth: 100,
               maxWidth: .infinity, minHeight: 0,
               idealHeight: 100, maxHeight: .infinity, alignment: .center)
        .background(Color.brown)
        .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
    }
    
}

struct managerView: View{
    var body:some View{
        VStack{
            Image("Rhino")
                .resizable()
                .aspectRatio(contentMode:.fit)
            Text("犀牛牛牛")
                .fontWeight(/*@START_MENU_TOKEN@*/.bold/*@END_MENU_TOKEN@*/)
                .font(.system(size:30))
        }
        .background(Color.brown)
        .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
    }
}
```

<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/HW3_img.jpeg">





