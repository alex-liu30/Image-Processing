I used a lot of general concepts (stuff that could be applied generally to most/all machines) and more specific concept-focused learning for each specific machine.

General Concepts

Image Processing Basics

Core Graphics and Core Image: Utilized these frameworks for rendering images and applying filters. Core Graphics is useful for low-level drawing, while Core Image provides higher-level image processing capabilities.

UIImage: The primary class used for image manipulation in iOS. It allows for easy loading, displaying, and converting images to different formats.

Color Spaces: Understanding RGB and grayscale color spaces was crucial for implementing effects like grayscale conversion and dithering.

Command-Line Interface (CLI)
User Input Handling: Used readLine() to capture user input from the terminal. Input was parsed into commands and parameters using string manipulation techniques.
Undo/Redo Functionality: Implemented using an array (imageStack) to maintain a history of image states. This allows users to revert or reapply changes easily.
File Handling: Used FileManager and URL to manage file paths and save processed images in various formats (e.g., PNG).

Tool-Specific Insights

Adaptive Thresholding
Adaptive Thresholding Specifically: Researched different thresholding methods, deciding on adaptive thresholding as I found its complexity interesting 
Binary Images: Tried to learn careful manipulation of pixel values to do this. Unsuccessful but I did  have "applyAdaptiveThreshold" that can be expanded to include more complex image processing techniques ie future enhancements.

Atkinson Dithering
Dithering Algorithms: Looked at dithering techniques online, particularly Atkinson dithering
Custom Error Diffusion Logic: Calculated  quantization error for each pixel and distributed it to neighboring pixels based on specific weights. 

Grayscale Converter with User-Specified Shades
Shades of Gray: Investigated how to convert RGB images into grayscale using different methods (average, luminosity) and how to control the number of gray shades.
User Interaction: Made the interface so that users could specify the number of shades.

Gaussian Blur and Laplacian Sharpening
Convolution Kernels: Learned about convolution operations and how they can be applied using kernels for blurring (Gaussian) and sharpening (Laplacian). 
Specified Regions + Performance Considerations: While implementing the specified regions feature, noted that (though fairly obvious) optimized performance is possible by limiting the area of convolution when applying effects only to specified regions. Pretty interesting and just a good thing to know for me, as doing this potentially may reduce any lag that may come from manipulating the whole image

High-Pass Sharpening
Image Decomposition: Explored techniques for decomposing an image into high-pass and low-pass components using Gaussian blur (used previous research -- see above -- to help me with this).

Motion Blur
Motion Blur Effects: Researched how to simulate motion blur based on an angle and radius, so I had to scour the internet for this kind of math-dependant integration

RGB Decomposition to Grayscale
Channel Manipulation: Learned how to manipulate individual RGB channels to derive grayscale values based on maximum or minimum channel intensities.
Image Representation: Explored how different approaches to channel selection affect the visual representation of grayscale images.

Single Color Channel Grayscale
Channel Selection Logic: Implemented logic to allow users to choose which RGB channel to use for grayscale conversion, enhancing flexibility in image processing.
