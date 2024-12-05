[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AmROh6B3)
# Coursework 1 - Deep Learning Module 2024

This repository and README contains relevant information regarding the Coursework 1 of the Deep Learning module, please read it all carefully. 

| **COURSEWORK** | **Date and time** |
| :------------------ | :---: |
| *Release* | Thursday 5 Dec 14:00h |
| *Due (deadline)* | Friday 6 Dec 18:00h |

**At 18:00h on Friday, I will clone your repositories, so make sure everything is committed by then!**


# Table of contents
1. [Assessment description](#description)
2. [Assessment format](#format)
3. [Deliverables](#deliverables)
4. [Tips and tricks](#tipsandtricks)
5. [Academic integrity](#academicintegrity)


## Assessment description <a name="description"></a>

For our first assessment, our goal is to solve an imputation problem: we will create a neural network architecture that learns how to recover missing portions of an image.

This is an important problem in magnetic resonance imaging (MRI), where patient scans are often limited to a few areas to avoid lengthy scanning times.

In particular, we are going to focus on images of human heads. We have managed to gain access to one hundred images of patient's heads but, unfortunately, these images have 
a significant portion of missing information. Your goal during the assessment is to design a neural network that can recover these missing portions.

We do not have access to the labels for the images we want to recover, so we will have to be a bit creative to obtain a workable dataset on which to train our neural network.

Fortunately for us, we have access to a generative model that has been trained to produce realistic-looking MRI images of patient's heads. Using this model, you will create an 
appropriate dataset to train your architecture. We have provided you with the basic setup code to start using this generative model in **Question 1**.

The corrupted images that we want to recover are contained in the numpy file `test_set.npy` of this repository. The file contains 100 patient images with a size of 64x64 pixels.

The architecture that you design in this assessment should use the artificially-generated dataset in order to recover the missing information in the images contained in `test_set.npy`.

## Assessment format <a name="format"></a>


A notebook file called `Assessment.ipynb` is provided for you to **solve** and **turn in** the assessment. All answers to the assessment should be contained within
the `Assessment.ipynb` notebook and **the name of the notebook should NOT be changed**. 

Inside the `Assessment.ipynb` file, you will find three questions. Please, do not change the structure the notebook, but you are free to 
add new code and text cells as required to your answers. Read the text for each question and follow the instructions carefully. 
Answers that do not follow this structure will not be marked.

Please, **make sure to execute all your cells and save the result of the execution**. We will only mark cells that have been executed and will not execute any
cells ourselves.


### Question 1 (25%)

Using the provided image-generation network, create a dataset of brain images that will later be used to train your chosen architecture. 

Given that you will likely want to use this dataset multiple times during training, we recommend that you save the generated images to an appropriate folder in your GDrive.

Once you have generated your dataset, load and display ten of your generated images in the notebook.

We have also provided you with some corrupted images in the file `test_set.npy` of this repository. You should also load and display ten of these corrupted images here.

Inside the notebook, we have provided template code, including some required downloads and installations, so that you can easily use the trained generative model. Sample generation in this model 
is done using the function `generate`, and is controlled by some input arguments. It is your job to figure out a sensible set of parameters that will produce images that are useful for the requirements of your task.

### Question 2 (25%)

Using the data generated in **Question 1**, create a PyTorch `TensorDataset` and a `DataLoader` for the training set. 

Using the provided corrupted images inside `test_set.npy`, create another `TensorDataset` and a `DataLoader` for the test set.

The training dataset should provide batches of brain images generated in **Question 1** and should corrupt these images appropriately so that they resemble images in the test set. The dataset should also pair each 
image with its corresponding un-corrupted image as a label.

The test dataset should provide the corrupted images provided, for which no labels are available.

Display in the notebook ten images of your training dataset and ten images of your test dataset, and their corresponding labels when available.

### Question 3 (50%)

Using the dataset created in **Question 2**, design and train an architecture to recover the missing image lines of the provided test dataset.

Once you have trained your architecture, display here ten images of the test set with the recovered lines filled in.

Additionally, save the test data with the missing values filled in into a numpy file called `test_set_nogaps.npy`. These images should be **in the same order** as those in the `test_set.npy` file and should have the same pixel size of 64x64. 
**Any images not contained in the `test_set_nogaps.npy` file or incorrectly ordered will not be marked.**

You have freedom to choose an architecture that you consider appropriate to solve this problem. However, you will need to train your chosen architecture as part of the assessment: **pre-trained networks are not allowed**.

You will be assessed by the quality of your predictions of the missing data values and additional marks will be given for originality in your network design choices. You should include, as part of your answer, a paragraph explaining the architecture 
you have chosen and any additional design choices and hyperparameters that have been important to build your solution.

This is an open-book assessment and you are encouraged to use resources online, including  tools like chatGPT. However, make sure to always mention the sources for your code and ideas, including websites, papers, and tools like chatGPT.


## Deliverables <a name="deliverables"></a>

As described in the description above, the assessment's deliverables are:

1. The completed `Assessment.ipynb` file - The name of the file should remain unchanged. The file should contain your answers to the three assessment questions.
The internal format of the notebook should also remain unchanged, but you are free to add new code and text cells as required to your answers. The notebook's cells
should be executed and saved: we will only mark cells that are executed and will not execute cells for you.

2. A generated `test_set_nogaps.npy` file - The file will contain 100 images corresponding to the 100 images contained in the provided `test_set.npy`. Each image will have the missing lines filled in by
your designed network. These images should be **in the same order** as those in the `test_set.npy` file and should have the same pixel size of 64x64. 
**Any images not contained in the `test_set_nogaps.npy` file or incorrectly ordered will not be marked.**

3. The completed `References.md` file - List in this file your references using the template provided. See the section on *Academic integrity* below.

4. Fill in the [Academic integrity declaration form](https://forms.office.com/e/hmFtcSeZUw) - Please, carefully read, fill, and submit this form in addition to your GitHub Classroom submission. See the section on *Academic integrity* below.


***IMPORTANT: When you save your notebook, make sure that all the cells are executed so that when you upload the `Assessment.ipynb` file to the repository, the output of the cells are visible***


## Tips and tricks <a name="tipsandtricks"></a>

- You have one day and a half: organise your time well and think about the tasks that you will need to do to complete the assessment before diving in. Then, build
a list of tasks, prioritise it and allocate time to each task in the list, including breaks and time to rest overnight. You can leave your networks training while you
sleep, but be careful not to burn all your compute units!

- Set up your development environment carefully: do not connect to a GPU and burn credits while you are writing code or doing other tasks that do not require
 serious compute.

- Checkpoint your models during training to avoid having to retrain from epoch 0 every time you disconnect your running environment.

- Test your submission early. In particular:
	- make sure you can save the `test_set_nogaps.npy` file correctly and upload it in the repository well before the deadline to void unpleasant last-minute surprises
	- make sure that, when you download your notebook from Colab with all the executed cells, these executed cells contain the output that you want to have visible in the final repository. If not, check that you have saved and uploaded the correct notebook.
 
 
## Academic integrity <a name="academicintegrity"></a>

This is an open-book assessment and you are encouraged to use resources online. 
However, we expect that you carefully review and understand every aspect of your submission (code, documentation, comments, etc.).
If you use AI tools, you should use them solely for learning, research, or understanding purposes rather than for directly solving assessment tasks.
We expect that all "human-readable" text in the assessment (including documentation, comments, and explanations) are written in your own words, accurately representing your personal understanding, knowledge, and opinions.
We also expect you to undertake this assessment individually and not discuss your answers with other students.

If you use any external sources outside the lecture notes, you should declare these in a `References.md` file and explained their usage in the code through comments and markdown, ensuring full transparency.
Populate the markdown file in the repository called `References.md` with links to sites you have used, papers you have read, links to your chatGPT prompts and answers, and any other resource that you have used to help you design your model.

At any point after the submission of your assessment, you may be invited to an oral examination to discuss or justify any aspect of your submission, 
and you should be prepared to explain any part of your work in detail if required.

As part of the assessment, it is **mandatory** that you fill in this [Academic integrity declaration](https://forms.office.com/e/hmFtcSeZUw).
**Assessments without a corresponding declaration will not be marked.**
