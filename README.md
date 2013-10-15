Kaggle-Grockit
==============

RBMs for Kaggle's "WhatDoYouKnow" competition

Code by Thomas Möllenhoff and Hubert Soyer.


How to use the code?
--------------------

To use the RBM described in the writeup you need to first create the dataset the RBMs operate on.

Download the compressed data from http://www.kaggle.com/c/WhatDoYouKnow/data and unpack it to the datasets folder.

The resulting folder should look like this: ./datasets/grockit_all_data/
Next, execute the data creation script that is located in ./code/datasetCreation:
    
    python create_dataset.py

The different RBMs can be accessed with the main.py located in ./code/RBMs.

The provided code operates on the validation datasets provided by Grockit.
The actual submissions were made with another dataset. (training.csv and test.csv instead of valid_training.csv and valid_test.csv) 
To train and predict on this dataset the code needs to be changed accordingly.


Some examples:

- Train non-factored RBM with bernoulli softmax visible units and standard parameters:
    
        python main.py 

- Train non-factored RBM with binomial softmax visible units and a with smaller learning rate (0.0002) for weights and biases:
    
        python main.py -x -r 0.0002 -v 0.0002 -z 0.0002

- Train factored RBM with 10 factors and 40 hiddens with binomial softmax visible units and CD-11:
    
        python main.py -t 1 -x -r 0.0002 -v 0.0002 -z 0.0002 -s 11 -n 40 -y 10

- Train conditional RBM with bernoulli softmax visible units:
        
        python main.py -t 2

- Help:
        
        python main.py --help
