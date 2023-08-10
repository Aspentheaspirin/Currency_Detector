# Currency_Detector

The purpose of this model is to identify the differences between three different forms of currency. It is trained to classify an image as either Euros, U.S. Dollars, and Japanese Yen. This makes it easier to figure out what a banknote is, compared to having to look through many different images online.

![add image descrition here](https://i.imgur.com/Z4jsNOu.jpg)![image](https://i.imgur.com/HxQXFX7.jpg)![image](https://i.imgur.com/vSjUgzI.jpg)

## The Algorithm

The detector works by uploading an image of the currency to a Jetson Nano and running it through the program. It uses the information it has gathered from the training to determine which catagory the image best fits in. The information gained from the detector can help someone figure out how much the bill is worth and where it can be used. 
## Running this project
**Launch VS Code.**

1. Click on the small green icon at the bottom left of your screen to access the SSH menu.
2. Select + Add New SSH Host to add a new host.
3. Enter ssh nvidia@x.x.x.x, replacing x.x.x.x.x with the IP address you usually use in Putty or terminal to connect to the Nano.
4. Pick the first configuration file.
5. Click Connect in the prompted window.
6. Choose Linux as the operating system when asked.
7. If you're asked to continue, click Continue.
8. You'll be asked for a password after connecting to the Nano. Input your Nano password and hit Enter.
9. Select Open Folder and navigate to jetson-inference. Input your password again if required.
10. Click Yes, I trust the authors to access and start working on your projects in this directory.

## Preping the Dataset.

1. Navigate to jetson-inference/python/training/classification/data.
2. Extract the dataset ZIP file.
3. Inside jetson-inference/python/training/classification/data, create a new folder called currency_detector. Inside currency_detector, add three folders: test, train, val, and a file named labels.txt.
5. In the train directory inside currency_detector, create 3 folders named euro, japanese_yen, and us_dollar.
6. Copy these folders to the val and test directories.
7. Distribute the images from your ZIP file among these folders, with 80% in the train folder, 10% in the val folder, and 10% in the test folder for each currnecy type. Unfortunately, this will be a manual task and may take some time.

## Training the Network

1. Go to the jetson-inference folder and run ./docker/run.sh.
2. Once inside the Docker container, navigate to jetson-inference/python/training/classification.
3. Run the training script with the following command: `python3 train.py --model-dir=models/currency_detector data/currency_detector --epochs=desired number of epochs`. Replace the "desired number of epochs" with how many epochs you want. This process may take quite some time.
4. You can stop the process at any time using Ctl+C and resume it later using the --resume and --epoch-start flags.
5. While still in the docker, run the code `python3 onnx_export.py --model-dir=models/currency_detector`. This is going to convert your model to the ONNX format.
6. Exit the docker by pressing **Ctrl + D**.

## Running the Model

1. Make sure you are in **jetson-inference/python/training/classification**.
2. Type the command `ls models/currency_detector/`. You should see a file titled resnet18.onnx.
3. Use the codes `NET=models/currency_detector` and `DATASET=data/currency_detector` to set the varibles.
4. To classify the image, run the comand `imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/FILE/INPUT.jpg OUTPUT.jpg`. Replace 'FILE' with the desired test file. Replace 'INPUT' with the desired input image. Replace 'OUTPUT' with the name of what you want the output to be.


[View a video explanation here](video link)
