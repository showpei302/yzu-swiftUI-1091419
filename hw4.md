<h1>HW4</h1>
    
```swift
import SwiftUI
struct ContentView: View {
    var body: some View {
        VStack {
            Text("Gaming Review App").font(.largeTitle).fontWeight(.heavy).foregroundStyle(.primary)
            TabView{
                Group{
                    Welcomeview().tabItem { Image(systemName: "rosette")
                        Text("Intro")}
                    GameListView().tabItem { Image(systemName: "rosette")
                        Text("GameList")}
                    CardView().tabItem { 
                        Image(systemName: "rosette")
                        Text("Term")
                    }
                    
                }
                .toolbarBackground(Color.black, for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)                
            }.tint(.yellow)
        }
    }
}





struct Welcomeview: View {
    var body: some View {
        VStack {
            Image("Intro").resizable().aspectRatio(contentMode: .fit)
            Text("This is an app that game overviews,including reviews from media outlets and user rating").font(.system(size: 22,weight:.bold, design: .rounded))
        }
    }
}







struct TermAndDescription:Identifiable {
    var id = UUID()
    var term:String
    var description:String
}
var myDictionary=[TermAndDescription(term: "MMORPG",description: "Massively mutiplayer onliune role-playing game"),TermAndDescription(term: "ARPG",description: "Action Role-playing Game"),TermAndDescription(term: "MOBA",description: "Multiplayer online battle areana")]

struct CardView: View{
    @State var currentCard = 0
    var body: some View{
        VStack{
            VStack{
                Text(myDictionary[currentCard].term).font(.title).padding(.all, 10)
                Text(myDictionary[currentCard].description).font(.body).foregroundColor(/*@START_MENU_TOKEN@*/.blue/*@END_MENU_TOKEN@*/).padding(.all,10)
                
            }
            .frame(minWidth: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealWidth: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, maxWidth: 300, minHeight: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealHeight: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, maxHeight: 300, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
            .background(Color.yellow)
            .onTapGesture {
                if currentCard<myDictionary.count-1{
                    currentCard+=1
                }
                else{
                    currentCard = 0
                }
            }
            Text("Tap to next card").padding(.all, 10)
        }
        
    }
    
}




struct Game:Identifiable {
    var id = UUID()
    var name:String
    var image:String
    var description:String
}

var Games=[Game(name: "FF14", image: "FF14", description: "MMORPG"),Game(name: "LOL", image: "LOL", description: "MOBA"),Game(name: "MapleStory", image: "Maple", description: "MMORPG"),Game(name: "MHR", image: "MHR", description: "ARPG"),Game(name: "Deadcell", image: "Deadcell", description: "Rough like ARPG")]

struct BasicImageRow: View{
    var thisGame:Game
    var body: some View{
        HStack{
            Image(thisGame.image).resizable().frame(width: 40, height: 40).cornerRadius(5)
            Text(thisGame.name)
        }
    }
}

struct GameDetailView:View{
    @Environment(\.presentationMode) var presentationMode
    var thisGame:Game
    var body: some View{
        ScrollView{
            VStack{
                Image(thisGame.image).resizable().aspectRatio(contentMode: .fill)
                Text(thisGame.name).font(.system(.title, design:.rounded)).fontWeight(.black)
                Spacer()
                Text(thisGame.description).font(.system(.subheadline, design:.rounded)).fontWeight(.light)
                Spacer()
            }
        }.overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label:{
                        Image(systemName:"chevron.down.circle.fill").font(.largeTitle).foregroundColor(.white)
                    }).padding(.trailing,20).padding(.top,40)
                    Spacer()
                }
            }
        )
    }
}

struct GameListView: View{
    @State var showDetailView = false
    @State var selectedGame:Game?
    var body: some View{
        NavigationView{
            List(Games){ gameItem in 
                BasicImageRow(thisGame: gameItem)
                    .onTapGesture {
                self.showDetailView = true
                self.selectedGame = gameItem
                }
            }.sheet(item: self.$selectedGame){thisGame in GameDetailView(thisGame: thisGame)}.navigationBarTitle("GameList")
        }
    }
}
  
```

[hw4demo](https://youtu.be/AtpBDaDq89M?si=yJJwurzhN-IgDKL4)
