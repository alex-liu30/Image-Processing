Here's the process I more or less followed doing this project:

1. Research and Planning
- Research image processing techniques relevant to each tool.
- Outline the desired functionality and expected input/output for each tool.
- Define the command structure for user interaction.

2. Coding Each Tool
- For each tool:
  - Implement the core functionality using appropriate Swift libraries (e.g., CoreGraphics, CoreImage).
  - Define functions that encapsulate specific image processing tasks.
  - Use enums and structs where necessary to improve code organization and readability.

3. User Interaction
- Implement a command-line interface that prompts users for input:
  - Ask for the path to the input image file.
  - Provide options for applying different effects and specify parameters (e.g., radius, angle, shades).
  - Allow users to specify regions of interest for certain effects.
 
Example (something likie this):

while true {
    print("Enter command:")
    guard let input = readLine()?.lowercased() else { continue }
    let components = input.split(separator: " ")

    // Check the first component for the command
    guard let command = components.first else { continue }

    switch command {
    case "grayscale":
        // Handle grayscale conversion
        if components.count > 1 {
            // Extract shades and optional region parameters
            let shades = Int(components[1]) // Example for shades
            // Additional logic to handle optional region parameters if provided
        }
    case "undo":
        // Handle undo action
        // Call undo function
    case "redo":
        // Handle redo action
        // Call redo function
    case "save":
        if components.count > 1 {
            let path = String(components[1]) // Example for save path
            // Call save function with path
        }
    case "revert":
        // Handle revert action
        // Call revert function
    case "quit":
        print("Exiting program.")
        exit(0)
    default:
        print("Unknown command. Please try again.")
    }
}


4. Undo/Redo Functionality
- Implement an undo/redo stack mechanism to manage changes made by the user:
  - Store previous states of images in an array or stack structure.
  - Allow users to revert changes or redo actions as needed.
 
Example (something like this):

var imageStack: [UIImage] = []
var currentIndex = 0

func applyEffect(image: UIImage) {
    // Apply effect and update stack
    if currentIndex < imageStack.count - 1 {
        imageStack.removeSubrange(currentIndex + 1..<imageStack.count)
    }
    imageStack.append(image)
    currentIndex += 1
}

func undo() {
    if currentIndex > 0 {
        currentIndex -= 1
    }
}

func redo() {
    if currentIndex < imageStack.count - 1 {
        currentIndex += 1
    }
}

5. Saving Output
- Provide functionality to save processed images:
  - Prompt users for output file paths.
  - Ensure proper handling of file formats (e.g., PNG).
 
Something like this woudl work for output:

func save(to path: String) {
    guard let data = imageStack[currentIndex].pngData() else { return }
    do {
        try data.write(to: URL(fileURLWithPath: path))
        print("Image saved successfully.")
    } catch {
        print("Failed to save image: \(error)")
    }
}

