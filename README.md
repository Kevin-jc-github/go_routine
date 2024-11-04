# Image Processing Pipeline in Go

This project is an image processing pipeline implemented in Go. It reads images, resizes them, converts them to grayscale, and saves them to a specified directory. The pipeline can run both with and without goroutines to compare the performance impact of concurrency.

## Features

- **Image Loading**: Loads images from specified paths.
- **Resizing**: Resizes images to a standard size (500x500).
- **Grayscale Conversion**: Converts each image to grayscale.
- **Image Saving**: Saves processed images to a new output directory.
- **Concurrency Toggle**: Choose to run the pipeline with or without goroutines.

### 1. Add Error Checking for Image File Input and Output
Error checking has been added to both the `ReadImage` and `WriteImage` functions. When an error occurs during image loading or saving, the function returns an error instead of panicking. This ensures that errors are properly logged and handled gracefully without crashing the program.

### 2. Replace Input Image Files
The default images used in the pipeline can be easily replaced by adding your desired images to the `images/` folder. The program reads all image paths provided, meaning you can specify any set of images you want to use without modifying the core logic.

### 3. Add Unit Tests to the Code Repository
Unit tests have been added in `image_process_test.go` to verify the key functions:
- **LoadImage**: Tests if images are loaded properly.
- **Resize**: Verifies that images are resized to the correct dimensions.
- **ConvertToGrayscale**: Tests the grayscale conversion.
- **SaveImage**: Ensures that processed images are saved without issues.

### 4. Add Benchmark Methods for Capturing Pipeline Throughput Times
Benchmark functions have been created to evaluate the throughput of the pipeline:
- The pipeline's performance is tested with and without goroutines, capturing execution times and providing a comparison between the two modes.

### 5. Design the Program to Run with and Without Goroutines
The main function accepts a command-line argument (`goroutines`) that determines whether to run the pipeline with or without goroutines. This feature allows easy performance comparison:
- **With Goroutines**: Stages of the pipeline run concurrently for faster processing.
- **Without Goroutines**: Each stage is executed sequentially.

### 6. Make Additional Code Modifications
The code has been enhanced to:
- Improve error handling and make the pipeline robust against potential issues.
- Handle nil images gracefully, ensuring the pipeline can proceed even if a single image fails.
- Add logging for better traceability of which images succeeded or failed during processing.

### 7. Build, Test, and Run the Pipeline with and Without Goroutines
The program includes a `runPipeline` function that is used to execute the image processing steps. By passing the appropriate command-line argument, you can run the program with or without goroutines and measure the elapsed time for each configuration. 

## Getting Started
### Prerequisites
- Go: Ensure you have Go (version 1.16 or later) installed on your system.
- Image Files: Place your image files in an images/ directory. The output images will be saved in images/output/.


##  Installation
### Clone the Repository:
https://github.com/Kevin-jc-github/go_routine.git
cd go_routine

## Run with Goroutines:

go run main.go goroutines


## Run without Goroutines:

go run main.go

## The following output demonstrates the difference in processing times with and without goroutines:
### Running with goroutines:
Success!

Success!

Success!

Success!

Pipeline completed in 10ms



### Running without goroutines:
Success!

Success!

Success!

Success!

Pipeline completed in 30ms



## Benchmarking
### To benchmark the performance of the pipeline with and without goroutines, run the following command:
go test -bench 

This will provide a comparative measure of the processing times in each mode.

## Unit Testing
### Unit tests are provided in the image_process_test.go file to verify each stage of the image processing pipeline.

### To run the tests:
go test -v

### Test Coverage
The unit tests verify the following:

- Loading Images: Ensures images are read properly without errors.

- Resizing Images: Verifies that the images are resized correctly to 500x500.

- Converting to Grayscale: Confirms the image is correctly converted to grayscale.

- Saving Images: Tests that processed images are saved successfully.
