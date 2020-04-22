# Making a List From A Simple Array in SwiftUI

## Fix Initializer 'init(_:rowContent:)' requires that 'String' conform to 'Identifiable'

The following will not work and will throw the error "Initializer 'init(_:rowContent:)' requires that 'String' conform to 'Identifiable'"
```Swift
import SwiftUI

struct ContentView: View {
    @State var array:[String] = ["a", "b", "c", "d"]
    var body: some View {
        List(array) { item in
          Text(item)
        }
        
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
```
Here is how to fix that. Simply add the following 3 lines of code:
```Swift
extension String: Identifiable {
    public var id: String { self }
}
```

Here is the final product:
```Swift 
import SwiftUI

struct ContentView: View {
    @State var array:[String] = ["a", "b", "c", "d"]
    var body: some View {
        List(array) { item in
          Text(item)
        }
        
    }
}

extension String: Identifiable {
    public var id: String { self }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
```
