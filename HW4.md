# HW4
ContentView
``` Swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("來買醉Bar")
                .font(.largeTitle)
                .fontWeight(.heavy)
                .foregroundStyle(Color.brown)
            TabView{
                Group{
                    WelcomeView()
                        .tabItem { 
                           Image(systemName: "storefront")
                            Text("Bar")
                        }
                    DrinksListView()
                        .tabItem { 
                            Image(systemName: "pencil.and.list.clipboard")
                            Text("Menu")
                        }
                    CocktailView()
                        .tabItem { 
                            Image(systemName: "wineglass.fill")
                            Text("Intro")
                        }
                }
                .toolbarBackground(Color.black, for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
            }
            .tint(.brown)
            
        }
    }
    
}

struct WelcomeView: View{
    
    var body: some View{
        VStack{
            Image("Bar")
                .resizable()
                .aspectRatio(contentMode: .fit)
            
            Text("我有酒\n你有故事嗎")
                .fontWeight(.heavy)
                .lineSpacing(5)
                .font(.system(size: 32.0))
                .foregroundColor(.white)
                .frame(width: 350,height: 100,alignment: .center)
                .background(Color.gray)
                .cornerRadius(20.0)
                .multilineTextAlignment(.center)
            
        }
    }
}
```
DrinksListView
```Swift
import SwiftUI

struct Drinks:Identifiable{
    var id = UUID()
    var name:String
    var image:String
    var description:String
}
var drinks = [
    Drinks(name: "NO.1 尼格羅尼", image: "Negroni", description: "苦甜重酒感的藥草調酒之王\n這杯苦甜調酒去年超車Old Fashioned，變成最受歡迎的經典調酒第一名"),
    Drinks(name: "NO.2 老古典", image: "Old Fashioned", description: "經典老派的熟悉滋味\n曾經連續8年是最受歡迎的調酒"),
    Drinks(name: "NO.3 瑪格麗特", image: "Margarita", description: "淚水與悔恨交雜的調酒\n瑪格麗特除了故事充滿傳奇，它也是美國數一數二受歡迎的調酒"),
    Drinks(name: "NO.4 咖啡馬丁尼", image: "Espresso Martini", description: "你該嘗試的經典咖啡調酒\n咖啡馬丁尼和黑色俄羅斯有點像，都是伏特加 + 咖啡的調酒"),
    Drinks(name: "NO.5 黛綺莉", image: "Daiquiri", description: "海明威也難以抗拒的清爽滋味\n以蘭姆酒為基底，黛綺莉如白玉般清透的酒液，搭配上微酸甜的口感，看似無害，後勁卻十分強烈"),
    Drinks(name: "NO.6 威士忌酸酒", image: "Whiskey Sour", description: "新手絕對入門調酒\n要選新手的第一杯調酒，這杯絕對是其中之一。\n不管是拿來喝或調製都是低門檻，很少聽說會有人覺得難喝"),
    Drinks(name: "NO.7 曼哈頓", image: "Manhattan", description: "優雅的調酒女王\n透過甜苦艾酒帶來類似綢緞般的口感，除了讓基酒本身的味道變得更加豐富之外，細膩的甜味也提高了整杯酒的層次感"),
    Drinks(name: "NO.8 莫希多", image: "Mojito", description: "清涼系飲品的不敗經典\n麻煩給我的愛人來一杯Mojito~\n我喜歡閱讀她微醺時的眼眸~")
]

struct BasicImageRow: View{
    var thisDrink:Drinks
    var body: some View{
        HStack{
            Image(thisDrink.image)
                .resizable()
                .frame(width: 40, height: 40)
                .cornerRadius(5)
            Text(thisDrink.name)}
    }
}

struct DrinksDetailView:View{
    @Environment(\.presentationMode) var presentationMode
    var thisDrink:Drinks
    var body: some View{
        ScrollView{
            VStack{
                Image(thisDrink.image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisDrink.name)
                    .font(.system(.title, design:.rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisDrink.description)
                    .font(.system(.subheadline, design:.rounded))
                    .fontWeight(.light)
                Spacer()}
        }
        .overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label:{
                        Image(systemName:"chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                    })
                    .padding(.trailing, 20)
                    .padding(.top, 40)
                    Spacer()
                }
            }
        )
    }
}

struct DrinksListView: View{
    
    @State var showDetailView = false
    @State var selectedDrink:Drinks?
    var body: some View{
        NavigationView{
            List(drinks){ drinkItem in 
                BasicImageRow(thisDrink: drinkItem)
                    .onTapGesture { 
                        self.showDetailView = true
                        self.selectedDrink = drinkItem
                    }
            }
            .sheet(item: self.$selectedDrink){thisDrink in DrinksDetailView(thisDrink: thisDrink)
            }
            .navigationBarTitle("酒單")
        }
    }
}
```
CocktailView
```Swift
import SwiftUI

struct NameAndIngredient: Identifiable {
    var id = UUID()
    var name: String
    var ingredient: String
    var imageName: String
}

var myDictionary = [
    NameAndIngredient(name: "尼格羅尼 Negroni", ingredient: "琴酒, 甜苦艾酒, 金巴利", imageName: "Negroni"),
    NameAndIngredient(name: "瑪格麗特 Margarita", ingredient: "龍舌蘭酒, 橙酒, 萊姆汁", imageName: "Margarita"),
    NameAndIngredient(name: "馬丁尼 Martini", ingredient: "琴酒, 不甜香艾酒", imageName: "Martini"),
    NameAndIngredient(name: "威士忌酸酒 Whiskey Sour", ingredient: "威士忌, 檸檬汁, 糖漿", imageName: "Whiskey Sour"),
    NameAndIngredient(name: "莫希多 Mojito", ingredient: "白萊姆酒, 檸檬汁, 糖漿, 蘇打水, 薄荷葉", imageName: "Mojito")
]

struct CocktailView: View {
    @State private var currentCocktail = 0
    
    var body: some View {
        VStack {
            VStack {
                Text(myDictionary[currentCocktail].name)
                    .font(.title)
                    .foregroundColor(.orange)
                    .padding(.all, 3)
                Text(myDictionary[currentCocktail].ingredient)
                    .font(.body)
                    .foregroundColor(.red)
                    .padding(.all, 3)
            }
            
            Image(myDictionary[currentCocktail].imageName) 
                .resizable()
                .aspectRatio(contentMode: .fit)
                .frame(width: 350, height: 350)
                .onTapGesture {
                    if currentCocktail < myDictionary.count - 1 {
                        currentCocktail += 1
                    } else {
                        currentCocktail = 0
                    }
                }
            
            Text("點擊圖片查看下一杯")
                .padding(.all, 10)
                
        }
        .padding(.bottom, 20)
        
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        CocktailView()
    }
}
```
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/hw4.1.jpg">
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/hw4.2.jpg">
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/hw4.3.jpg">
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/hw4.4.jpg">
