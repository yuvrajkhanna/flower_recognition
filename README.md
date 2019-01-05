# flower Recognition

we print out location of our python file using this command.<br/>
**os.listdir** will give names of all files in the location given to it.<br/>
![](images/2.png)

**os.path.join** simply joins location we do this so we can loop through each folder in flowers<br/>
those files in that location which ends with jpg will go through if statement.<br/>
simply get images from that folder resize it to given size then store them in image_train.<br/>
![](images/3.png)

now since we have stored our data folder wise all training examples of same category are together<br/>
now that is not a good practice so what we do is we zip together pixel values of images and thier categories.<br/>
then rearrange them in random order<br/>
then get back train data(pixels) and labels.<br/>
![](images/4.png)

now since given labels are strings we cant put them in model so we have to 1st convert them into intergers.<br/>
it is automatically done by **label_encoder**.<br/>
once they are integers we use **one-hot_encoding**.<br/>
it basically converts 3 to (0,0,0,1,0) and 1 to (0,1,0,0,0)..... <br/>
**there are four 0s and one 1 because total no of categories are 5**
![](images/5.png)

split date into 2 parts to use 2nd part for validation I have used 0.9-0.1 split in out case.<br/>
we do this to make sure our model is not **overfitting**.<br/>
![](images/6.png)

created a simple model.<br/>
here in 1st line when we add **conv2D layer** --><br/>
we have to mension imput_size of each image in our 1st layer of our model.(28x28x1)<br/>
our image has its **depth 3** that is why there is 64x64x3 image not 64x64.<br/>
coloured images are usually represented with RGB that is **depth 3**.<br/>
**filters** mean depth of our layer after convolution.<br/>
**kernel_size** is filter size that convolve over our image.<br/>
**padding** is 0s we put to have image of size we want after convolution.<br/>
it is good to use activation after every conv layer so we use **relu activation** as it is very less coputationally expensive.<br/>
this ends our **convolutional layer**.<br/>
**max pool layer** simpy chooses maximum from its filter nothing to explain.<br/>
**dropout layer** is used to avoid overfitting.<br/>
**flatten** converts the tensor like output from conv layers to a vector which can be used in **dense(simple neural net)** layer.<br/>
our last layer have only 10 units as our output is a vecotor of (1x10).<br/>
since it is last layer we can use better activation that is softmax
![](images/7.png)

set your optimizer that will do your **gradient descent** step.(better if you use **Adam** as it converges faster)<br/>
![](images/8.png)

pass your **optimizer** and also choose your **loss function** and **metrics** and compile your model<br/>
![](images/9.png)

if your loss is almost constant then this wil reduce learning rate so it can improve further.<br/>
![](images/10.png)

we can create more data by **data augementation** method which simpy changes images little bit<br/>
solving our problem of having less data. :) <br/>
![](images/11.png)

train the model(by the way verbose means how you want to show training process)<br/>
![](images/12.png)

please share if this helped :)
