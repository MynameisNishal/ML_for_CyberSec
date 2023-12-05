# ML_for_CyberSec

## Running the Code

To run this project, follow the steps below:

1. Upload the `lab4.ipynb` notebook to Google Colab or Jupyter Notebook environment.
2. Ensure the following data files are uploaded to your Google Drive:
    - BadNet weights file
    - Benign data content (`valid.h5` and `test.h5`)
    - Poisoned data content (`bd_valid.h5` and `bd_test.h5`)
3. Mount your Google Drive in the Colab notebook to access the datasets:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
4. Set the file paths in the `lab4.ipynb` notebook to match the locations of your data files in Google Drive. Replace path-in-drive with the actual path to your files:
   ```python
    Clean_Data_Path = '/content/drive/MyDrive/Lab3/cl/valid.h5'
    Clean_Test_Data_Path = '/content/drive/MyDrive/Lab3/cl/test.h5'
    Poisoned_data_path = '/content/drive/MyDrive/Lab3/bd/bd_test.h5'
    model_file = '/content/drive/MyDrive/Lab3/models/bd_net.h5'
    model_weights = '/content/drive/MyDrive/Lab3/models/bd_weights.h5'
## Introduction

The increasing reliance on neural networks in various applications has raised significant concerns regarding
their security, particularly from backdoor attacks. These attacks, which subtly manipulate network behavior,
pose a critical threat to the integrity of neural network applications. This report details the development
of a novel backdoor detector designed to safeguard BadNets, a type of compromised neural network, using
a dataset derived from YouTube Faces. The primary defense mechanism employed is network pruning, a
technique aimed at enhancing model robustness against such insidious threats.

## Dataset


In this experiment, the YouTube Face dataset is partitioned into two distinct subsets: clean and poisoned.
The clean subsets, specifically the validation and test sets named ”valid.h5” and ”test.h5,” are employed for
fine-tuning and evaluating the model’s performance. To simulate backdoor attacks, poisoned datasets featuring
a sunglasses trigger - labeled as ”bd valid.h5” and ”bd test.h5” - are utilized to test the efficacy of the defense
mechanism

## Methodology

In this project, a pruning defense was applied to a neural network, strategically eliminating channels according
to their activation intensities. This pruning process continued until the model’s accuracy declined by specific
predefined thresholds, set at 2%, 4%, and 10%. Utilizing TensorFlow and Keras for implementation, the
performance of the pruned models was assessed against both the unaltered and the poisoned datasets. The
evaluation focused on the models’ ability to distinguish between clean and backdoored inputs, relying on the
level of agreement between the model predictions. The primary goal of this strategy was to find an optimal
balance between maintaining accuracy and efficiently detecting backdoor attacks

1. . Environment Setup and Essential Libraries: The project commenced with the setup of a Python
environment and the importation of key libraries. TensorFlow and Keras were utilized for neural network
modeling, NumPy for numerical computations, Matplotlib for visualizations, and OpenCV for image
processing.

2. Data Integration and Loading: The project leverages Google Colab for its computational needs. A
custom ’data loader’ function was created to handle the YouTube Face dataset, ensuring efficient data
management and preprocessing. This function is vital for preparing the dataset for subsequent training
and analysis.

3. Data Loader Function Implementation: The ’data loader’ function is instrumental in reading the
dataset, modifying its structure to suit the requirements of the neural network, and ensuring the data is
in a format that is ready for model input.

## Results

![My Image](./results.jpg)


The experiment focused on implementing a pruning defense in a neural network to counteract backdoor
attacks. This process involved selectively removing channels based on their activation levels and monitoring the
consequent impact on accuracy. The pruning was executed until the model’s accuracy experienced predefined
thresholds of reduction at 2%, 4%, and 10%. The evaluation of the pruned models was conducted using
TensorFlow and Keras, assessing their performance against both original (clean) and poisoned datasets.

### Pruning Results:

1. Initial Accuracy Thresholds: The pruning process was structured to halt upon reaching specific accuracy
drop thresholds. The experiment successfully saved different versions of the model corresponding to
these accuracy decreases.

2. Model Performance: The model demonstrated a distinct drop in accuracy at each predefined threshold. The results indicate that the model was saved after each significant accuracy drop, ensuring a comprehensive evaluation of the pruning defense at various stages.

3. Output Summary:
   
During the pruning process, the following outcomes were observed and logged:
    (a) 2% Accuracy Drop: The model was saved after reaching at least a 2% drop in accuracy.
    (b) 4% Accuracy Drop: Subsequently, the model experienced a further accuracy decline of at least 4%,
        prompting another save.
    (c) 10% Accuracy Drop: Finally, the model was saved after a substantial accuracy reduction of at least 10
    
The results show that the pruning defense was effective in manipulating the model’s accuracy, providing
insights into the balance between model accuracy and backdoor attack resilience. The saved models at different
accuracy levels facilitate a nuanced analysis of the trade-offs involved in implementing pruning defenses in
neural networks.


