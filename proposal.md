# Project Proposal

 
### **Client:** <br>

The client is a large student loan processer. <br>

***

### **Question/Need:**<br>


The company receives thousands of correspondance per day. Correspondance comes in the form of emails, faxes, web forms and letters. Each correspondance must be routed to the correct department for processing.Currently, this process is done by hand and requires a department to keep up with the volumes of documents.
<br>

The goal of this project is generate a classification model to help automate the document coding/routing process.
<br>

***

### **Data Description:**<br>

The data I will be using are example images of documents that would need to be classified with their document code.<br>
***

### **Solution Path:**<br>
This problem is complex and will require engineering to solve. Issues and solutions identified below:

- Data (There is not a large dataset of filled documents)
  - We will start by manually gathering template versions of the documents
  - Then using OpenCV we will add pseudorandom text to the images to simulate filled forms
  - These "filled forms" will then be randomly augmented using distortion, noise and masking. 
  - This combination of tooling will allow us to create an arbitrary number of samples for each class and should help simulate poor quality and noisy production images
- Preprocessing
  - If not already, images will need to be converted to greyscale
  - Images will need to be resized to a consist size ie. 80x80
  - **Feature Engineering**
    - Option 1: Flatten image to create 1 "row" of data with each column being a different pixel
    - Option 2: We use a pretrained image model such as [Document Transformer](https://huggingface.co/spaces/microsoft/document-image-transformer) to create embeddings for the images. The model could then be trained on those embeddings. 
- Model
  - Logistic Regression
  - Tree Based Model
  - *NN*
    - Utilize pretrained image model and add a classification layer
<br>

***

### **Criteria for Success:**<br>

Document coding efficiency can be increased by 20% without increasing accuracy from the current 88%.
- We can reach 90% precision on 20% of samples for a given class. 
<br>

***

### **Assumptions and Risks:**<br>

Our data augmentation strategy will generalize to real life incoming documentation.
<br>

We risk biased misclassification of documents.
<br>
***

### **Tools:**<br>
Sklearn will be used for modeling. 

Pytorch/huggingface may be used for modeling or embedding.

OpenCV will be used for image processing.

Gradio may be used for creating a demo app. Alternative could be FastAPI and Angular. 

<br>

***

### **Communication:**<br>
A slide presentation will be made explaining the model building process and showcasing the model utility.

A demo web app will be presented allowing for live demonstration of the tool. 

<br>

***

### **MVP Goal:**<br>

An MVP for this project will consist of a Logistic Regression fit on flattened pixel values of the images.
