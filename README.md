# tinyCamML (Spatial Extent of Sunny Day Flooding)
 Sensor system for detecting tidal flooding on roads in coastal communities using TinyML

## ML Pipeline

### Binary Classification

Included are notebooks for training, testing, and quantizing MobileNetV2 based models for binary classification of flooded/not_flooded.

#### mobilenetv2_training.ipynb
A training notebook to create a binary classification model based on mobilenetv2, to be used with input images of 224x224. 

#### ModelTester.ipynb
A testing notebook to test any models you have trained. Allows you to load a model, use it to generate predictions on images you choose, generate f1 scores, generate confusion-matrices, and generate GradCAM overlays of predictions from the model.

### Segmentation

#### Unet_model_trainer.ipynb
A training notebook to be used with images that have been labeled with [Doodler](https://github.com/Doodleverse/dash_doodler).

Use Doodler to "doodle" images with their classes. For this project the following classes were used: water, road, building, sidewalk, people, other. Use class_remapper.ipynb to consolodate classes to: water, road, neither. 

Use the "gen_images_and_labels.py" utility from Doodler to create two folders containing the images and labels from your doodled images. Move these folders to data->segmentation as shown in the directory structure below.

Directory structure for training:
```
──data─┬─classification─┬──flooded
       │                └──not_flooded
       │
       └─segmentation───┬──images──images
                        └──labels──labels
```

### Model Deployment

Models can be converted to the flatpack .tflite format using the model_converter and model_converter_segmentation notebooks.
Both notebooks require a representative dataset to quantize to UINT8/INT8. 

### Utilities

#### filename_scraper.ipynb
This notebook will create a CSV of all files located in a directory. Useful for creating a csv of the filenames of your labeled images for tracking.

#### class_remapper.ipynb
This notebook can be used to remap classes from labeled doodles. Open the notebook, choose an image, configure the remapper, and remap.
Currently it is a manual process. Future version of this util will allow a user to select a directory of images to remap.
 
## Camera Module
Documentation for the camera module will be available soon.

## Communications Hub
Documentation for the communications hub will be available soon.
