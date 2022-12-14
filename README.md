# Biosignals-with-TinyML
Set EMG signals as an example in the plantform Edge Impulse (From Upload to Deploy)

## 1. Resgister an Account of Edge Impulse and Log in
by clicking here: https://studio.edgeimpulse.com/login

## 2. Create a New Project
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/1.png)  
Firstly, click the green button **+ Create new project**  
Then, name your project and choose its type (usually 'Developer')  
Last, click the green button below "Create new project"  

## 3. Acknowledge of the Dashboard
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/2.png)  
By reading the article here: https://docs.edgeimpulse.com/docs/edge-impulse-studio/dashboard

## 4. Process Your Data
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/3.png)  
To upload any data to Edge Impulse, you'll need to deliver the data in the Data acquisition format: https://docs.edgeimpulse.com/reference/data-ingestion/data-acquisition-format  
Here, we chose the data form of **CSV**. And it must have the titles of "timestamp" and the data name in the first line  

## 5. Upload Your Data
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/4.png)  
Let's click **Data acquisition** on the left side  
Then, click **Upload data** on the top  
After that, **Select files** >> **Upload into category** >> **Label**
Last, click **Begin upload** button below  
If everything goes well, you will see the outcome: "Job completed"  
The progress of Step 5 can be repeated several times if you have different data to upload

## 6. Split Your Data into Smaller Samples
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/5.png)  
Let's turn to the training/test data by clicking the top label of "Training data" & "Test data" here  
After that, We need to click the 3 dots here  
Then, click **Split sample**  
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/6.png)  
Each white box is the length of a single sample after data segmentation, and we can drag and stretch boxes to resize and reposition samples, aand increase and decrease samples' quantity.

## 7. Create Impulse
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/7.png)  
Click **Create Impulse** on the left side  
(There is a detailed explanation about the parameters in this section???https://docs.edgeimpulse.com/docs/edge-impulse-studio/impulse-design)  
Firstly, it is needed to set the parameters of **Windows size** , **Window increase** and **Frequency**  
Secondly, **Add a processing block** ("Flatten" is the best choice for EMG)  
Thirdly, **Add a learning block** (Here we do the "Classification" of motion)  
Finally, click **Save Impulse** button  

## 8. DSP (Digital Signal Processing)
(All the method of DSP can be learned through: https://docs.edgeimpulse.com/docs/edge-impulse-studio/processing-blocks)  
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/8.png)  
Click the name of the processing block you chose in Step 6 in the left side (Here we take "Flatten" as an example)  
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/9.png)  
Set parameters of DSP >> Click "Save parameters" button >> "Generate features"

## 9. Data Training & Test
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/10.png)  
Set the NN parameters like epoch, Learning rate an Validation set  
Then, build the NN architecture  
Clike "Start training" button to finish, and you will see the results on the right side after a few minutes  
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/11.png)  
You can test your model in the "Model testing" with your test data

## 10. 2 Ways to Deploy the Model on the **Tensorflow lite** Supported MCU
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/12.png)  
### The first way is to create a liberary
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/13.png)  
For example, we can create an Arduino liberary and add it to the original liberary files  
Thus, we can directly call the relevant library during programming  
### The second way is to build a "ready-to-go binary" firmware
![image](https://github.com/Zachay-NAU/Biosignals-with-TinyML/blob/main/IMG/14.png)  
We can directly drop the firmware into the device storage after it enters the boot mode  
The tips will show in the serial port
