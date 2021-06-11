# Face_Recognition

## Code Structure

```
Face_Recognition/
  ├── face_detect.py
  ├── face_rec
  │   ├── face_capture.py
  │   ├── face_rec.pb
  │   ├── face_rec_train.py
  │   └── train_images
  ├── face_rec.py
  └── opencv_face_detector
      ├── deploy.prototxt
      ├── opencv_face_detector.pbtxt
      ├── opencv_face_detector_uint8.pb
      ├── res10_300x300_ssd_iter_140000_fp16.caffemodel
      └── weights.meta4
```

## Capture Sample Images for Training

- Run the script `face_capture.py` to capture images from the video camera.
```
$ python face_capture.py
```

- Save the cropped images.
This script saves the cropped face images in `face_rec/outputs` directory. 

## Train the network with new data

1. Save train images

Save train images in the directory `face_rec/train_images`.
Images for each person should be separated by the folder named `{Person_Name}`.

```
train_images/
  ├── Person_1
  │   ├── face_0001.png
  │   ├── face_0002.png
  │   ├── ...
  │   └── face_0300.png
  ├── Person_2
  └── etc.
```

2. Run `face_rec_train.py` and update `face_rec.pb` file.

- Sample Usage
```
$ python face_rec_train.py --num_epochs 200 --minimum_cost 5e-06
```

## Test with the camera.

- Run the script `face_rec.py` and check the name of recognized face.
```
$ python face_rec.py
```
