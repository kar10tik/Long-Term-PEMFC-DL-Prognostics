# Long-Term-PEMFC-DL-Prognostics

This repository contains the datasets used and the machine learning models implemented in Python 3 for long-term degradation prognostics of proton exchange membrane fuel cells (PEMFCs) in the paper "*Accurate long-term prognostics of proton exchange membrane fuel cells using recurrent and convolutional neural networks*", published in the International Journal of Hydrogen Energy. 

If you use the code in your research, please cite the paper as:

*Sahajpal K, Rana KPS, Kumar V. Accurate long-term prognostics of proton exchange membrane fuel cells using recurrent and convolutional neural networks. Int J Hydrogen Energy 2023. https://doi.org/10.1016/j.ijhydene.2023.04.143.*

Running the code only requires an elementary knowledge of Python. But to experiment with model implementation and hyperparameter optimization, you might need to refer to the documentation of the associated libraries (keras, sklearn, numpy, optuna, etc.).

# Usage
 
The IEEE 2014 PHM Challenge dataset files for the PEMFC stack operated with and without current ripples are provided with this repo in the folders "FC1_Without_Ripples" and "Full_FC2_With_Ripples" within IEEE 2014, respectively. To test/implement the deep learning models in Google Colab:

1. Open the **PEMFC_Prognostics.ipynb** file in Github and click **Open in Colab**.
2. Connect to a Colab runtime, preferably a GPU one as model training and optimization are compute-intensive. 
3. Add the dataset files to a Google Colaboratory runtime. There are two ways to do this: 
    1. Add the dataset files to your Google Drive. The code assumes that you add the dataset files in the topmost Google Drive directory. If the datasets are at a different path, modify the path in `pd.read_csv()` in the **IEEE PHM 2014 Data Challenge** code cells.
    **OR**
    2. Create a shortcut to [this Drive link](https://drive.google.com/drive/folders/19MgM4AyMeHZGXDILrIF8HT9K8Ki1vjDz?usp=sharing) in Google Drive. To do so, click the down arrow near the folder name following **Shared with me** and click **Add Shortcut to Drive**.
4. Mount Google Drive by running the *Mount Google Drive* cell.
3. Run the **Requirements** cells and allow Google Colab access to Google Drive when mounting.
4. You can experiment with neural network model structures under **Model Implementation**. To experiment with the varying training-validation-dataset sizes, use the `train_test_split()` function under **Dataset Preprocessor**. 
5. To evaluate the dataset performance with the optimum hyperparameters reported in the paper up to 4 significant digits, run the **Preprocess the Dataset** and **Model Evaluation** code cells without tweaking anything in Step 4.
6. To optimize the model hyperparameters, you can configure the functions in `class optuna_search()` under **Hyperparameter Optimization**. Please refer to the (Optuna documentation)[https://optuna.readthedocs.io/en/stable/index.html] for more information on the functions involved.
    1. You can change the network optimizer hyperparameters for RMSprop/Adam/SGD Optimizers in the `create_optimizer` function definition.
    2. You can select the model to optimize and define the hyperparameter search spaces for the number of convolutional filters, dropout, number of neurons in each hidden layer, and activation function in the `objective_function` function definition.
    3. You can choose how many optimization trials you want to run by changing `n_trials` in the `optimize_study` function definition. You can also select hyperparameter optimizers other than tree-structured Parzen estimators (TPE) and pruners other than Hyperband within `optimize_study`.

For any questions, you can reach out to me at my email address on my GitHub profile.