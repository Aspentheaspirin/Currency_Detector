# Currency_Detector

The purpose of this model is to identify the differences between three different forms of currency. It is trained to classify an image as either Euros, U.S. Dollars, and Japanese Yen. This makes it easier to figure out what a banknote is, compared to having to look through many different images online.

![add image descrition here](https://i.imgur.com/Z4jsNOu.jpg)![image](https://i.imgur.com/HxQXFX7.jpg)![image](https://i.imgur.com/vSjUgzI.jpg)

## The Algorithm

The detector works by uploading an image of the currency to a Jetson Nano and running it through the program. It uses the information it has gathered from the training to determine which catagory the image best fits in. The information gained from the detector can help someone figure out how much the bill is worth and where it can be used. 
## Running this project
Launch VS Code.

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

[View a video explanation here](video link)
