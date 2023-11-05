# HW1
```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Image("Photo")
                .resizable()
                .aspectRatio(contentMode: .fit)
                .overlay(
                    Text("1091452 張繽 \n他摸起來毛毛的")
                        .fontWeight(.heavy)
                        .lineSpacing(10)
                        .font(.system(size: 20))
                        .foregroundColor(.white)
                        .background(Color.gray)
                        .frame(width: 400, height:100)
                        .cornerRadius(30)
                        .opacity(0.8)
                    ,alignment: .bottom
                )
                .overlay(
                    Image(systemName: "carrot.fill")
                        .font(.system(size:50))
                        .foregroundColor(.red)
                        .shadow(color: .orange, radius: /*@START_MENU_TOKEN@*/10/*@END_MENU_TOKEN@*/, x:5.0, y: 2.0)
                    ,alignment: .top
                )
        }
    }
}
```
<img src="https://github.com/Zh0B/YZU-swift-1121/blob/main/HW1_img.jpeg">
