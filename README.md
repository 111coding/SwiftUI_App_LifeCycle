# SwiftUI_App_LifeCycle

```swift
import SwiftUI

@main
struct ApplinkTextApp: App {
    
    @Environment(\.scenePhase) var scenePhase
    
    init(){
        print("App Initialize")
    }
    
    var body: some Scene {
        
        WindowGroup {
            ContentView()
                .onOpenURL{ url in
                    // Opened from Scheme
                    print(url)
                }
        }.onChange(of: scenePhase) { newScenePhase in
            switch newScenePhase {
            case .active:
              print("App is active")
            case .inactive:
              print("App is inactive")
            case .background:
              print("App is in background")
            @unknown default:
              print("Oh - interesting: I received an unexpected new value.")
            }
        }
       
        
    }
}
```
