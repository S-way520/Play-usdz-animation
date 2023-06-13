# The first part
![IMG_0099](https://github.com/S-way520/Play-usdz-animation/assets/95877651/924b49bb-2f45-4c4c-8775-769a90716dab)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import RealityKit
struct ContentView: View {
    var body: some View {
        RealityView()
            .edgesIgnoringSafeArea(.all)
    }
}
struct RealityView: UIViewRepresentable {
    func makeUIView(context: Context) -> ARView {
        let arView = ARView(frame: .zero, cameraMode: .ar, automaticallyConfigureSession: true)
        let anchorEntity = AnchorEntity(plane: .horizontal)
       guard let ARentity = try? ModelEntity.load(named: "toy_biplane_idle") else {
            fatalError("toy_biplane_idle model is not!")
        }
        ARentity.playAnimation(ARentity.availableAnimations[0].repeat(duration: .infinity), transitionDuration: 0.5, startsPaused: false)
        anchorEntity.addChild(ARentity)
        arView.scene.anchors.append(anchorEntity)
        return arView
    }
    func updateUIView(_ uiView: ARView, context: Context) {}
}
```
