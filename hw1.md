<h1>HW1</h1>
    
```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        Image("B")
            .resizable()
            .aspectRatio(contentMode: /*@START_MENU_TOKEN@*/.fill/*@END_MENU_TOKEN@*/)
            .overlay(
                Text("享受當下吧！")
                .fontWeight(.heavy)
                .lineSpacing(20)
                .font(.system(size: 32.0))
                .foregroundColor(.black)
                .frame(width:350, height:150,alignment:.center)
                .background(Color.white)
                .cornerRadius(30.0)
                .opacity(0.8)
                ,alignment: .bottom
                )
            .overlay(
                Image(systemName: "square.and.arrow.up.circle")
                    .resizable(capInsets: /*@START_MENU_TOKEN@*/EdgeInsets()/*@END_MENU_TOKEN@*/, resizingMode: /*@START_MENU_TOKEN@*/.stretch/*@END_MENU_TOKEN@*/)
                    .frame(width: 50, height: 50, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                    .position(x:400.0, y:600.0) 
                )
            .overlay(
                Text("1091419          江奇倫").fontWeight(.heavy).position(x: 270,y:50)
                
            )
            
        
    }
}



    
```

<img width="40%"  src="https://raw.githubusercontent.com/ncudemo/yzu-swiftui-1121-864106/main/hw1-20231002-1.png">
