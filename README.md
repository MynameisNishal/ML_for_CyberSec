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
