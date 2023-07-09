# Sign Language Detection using YOLOv8

## Introduction
Welcome to the Sign Language Detection project! This project focuses on detecting the 26 letters of the alphabet along with two additional classes: space and delete. The purpose of this project is to build a chat bot that uses sign language to facilitate communication for disabled individuals. In this project, we utilized the YOLOv8 pre-trained model to train on our custom dataset.

## Prerequisites
Before getting started, ensure that you have the following requirements fulfilled:
- Python 3.x installed on your system.
- GPU (recommended) or CPU with sufficient power to run the YOLOv8 model.
- The necessary Python libraries installed. You can install them by running `pip install -r requirements.txt`.

## Dataset Preparation
To train the YOLOv8 model, you need a labeled dataset containing images of sign language gestures along with their corresponding bounding box annotations. The dataset should be organized in the following structure:
```
dataset/
    ├── images/
    │   ├── image1.jpg
    │   ├── image2.jpg
    │   └── ...
    └── labels/
        ├── image1.txt
        ├── image2.txt
        └── ...
```
- The `images` directory contains all the training images.
- The `labels` directory contains the annotation files for each image in YOLO format. Each annotation file should have the same name as its corresponding image file, but with a `.txt` extension.

The annotation file format follows the YOLO format, which consists of one row per object detected in the image. Each row contains the object class index (integer), normalized bounding box coordinates, and should be space-separated. The format for each row is as follows:
```
<class_index> <x_center> <y_center> <width> <height>
```
Note: The bounding box coordinates should be normalized by dividing them by the image width and height.

## Model Training
To train the YOLOv8 model on your custom dataset, follow these steps:

1. Download the pre-trained weights for the YOLOv8 model. You can obtain them from the official YOLO repository or other reliable sources.
2. Place the downloaded weights file in the project directory.

3. Run the training script by executing the following command:
   ```
   python train.py --data dataset/data.yaml --cfg cfg/yolov8.cfg --weights <path_to_pretrained_weights>
   ```
   Make sure to replace `<path_to_pretrained_weights>` with the actual path to the pre-trained weights file.

4. The training process will start, and you will see the progress and loss information displayed on the console. The model will be saved periodically during training.

5. Once the training is complete, you will find the final trained weights in the `weights` directory.

## Model Inference
To use the trained YOLOv8 model for sign language detection, you can follow these steps:

1. Place the trained weights file (`best.pt`) in the `weights` directory.

2. Run the inference script by executing the following command:
   ```
   python detect.py --source <path_to_input_video_or_image> --weights weights/best.pt --names data/classes.names
   ```
   Replace `<path_to_input_video_or_image>` with the path to the input video or image you want to perform sign language detection on.

3. The script will process the input and generate the output with bounding box annotations and class labels (letters of the alphabet, space, delete) if any are detected.

4. The output will be displayed on the screen or saved to a file, depending on the provided command-line arguments.

## Integration with Chat Bot
To integrate the sign language detection capabilities into your chat bot, you can utilize the output from the inference script in the following way:

1. Configure your chat bot to accept input from sign language gestures, either through image or video inputs.

2. Connect the output of the inference script to your chat bot's input processing module. Extract the detected class labels (letters of the alphabet, space, delete) from the output.

3. Map the detected class labels to their respective meanings in the chat bot's response generation module.

4. Use the extracted information to generate appropriate responses and facilitate communication for disabled individuals through sign language.

## Conclusion
Congratulations! You now have a sign language detection system based on YOLOv8, capable of detecting the 26 letters of the alphabet, along with space and delete gestures. By integrating this system into your chat bot, you can provide a more inclusive communication experience for disabled individuals. Feel free to experiment, refine, and expand upon this project to suit your specific requirements. Enjoy building and making a positive impact in the world of sign language communication!
