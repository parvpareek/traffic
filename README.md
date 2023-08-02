# traffic
Classifies road signs using CNN 

## How To Run
Execute the command python traffic.py directory_name.

Replace directory_name with the training data directory

## Training Data
Download the training data set from [here](https://cdn.cs50.net/ai/2020/x/projects/5/gtsrb.zip) or provide your own using .ppm files. The folder containing the images should be names after the type of road sign it represents. 

### Requirements
Run pip3 install -r requirements.txt

### 1. Convolutional and Pooling Layers

Initially, the CNN model consisted of one Conv2D layer (3x3 kernel) followed by one max-pooling layer (2x2 pool size).

First, I experimented with different numbers of convolutional and pooling layers. The best-performing configuration was found to be 2 Conv2D layers (3x3 kernel) followed by 2 max-pooling layers (2x2 pool size), which resulted in improvements. Further increasing the layers to 3 Conv2D and 2 max-pooling didn't yield better results.

### 2. Number and Sizes of Convolutional Filters

Next, I investigated the impact of changing the number and sizes of filters in the Conv2D layers. Doubling the number of filters to 64 resulted in worse performance. Reverting to the original number of filters for the first layer (64) while keeping the second layer at 32 filters again led to worse results. Switching the filter sizes from 3x3 to 5x5 also had negative consequences.

The best configuration for the filters was found to be 2 Conv2D layers with 64 filters in both layers and a kernel size of 3x3, which performed better.

### 3. Pooling Layer Size and Hidden Layers

Changing the pool size to 3x3 or 1x1 led to disastrous results, indicating that the original 2x2 pool size was optimal. The experiment with different hidden layer sizes also provided insights. Reducing the hidden layer to 50 resulted in worse performance. Increasing the hidden layer size to 128 caused a slight decline in performance, while adding more hidden layers of the same size yielded slightly worse results.

The best configuration was achieved with two Conv2D layers (32 filters, 3x3 size), two pooling layers (2x2 size), and two hidden layers with a size of 256, which delivered better performance.

### 4. Dropout

Lastly, I experimented with dropout values. Decreasing the dropout from 0.5 to 0.3 improved performance during training, but testing accuracy remained the same. Setting dropout to 0.1 increased performance during training, but testing accuracy slightly decreased. Increasing dropout to 0.8 caused a slight decrease in performance.

In conclusion, the optimized CNN configuration that delivered better performance included 2 Conv2D layers (32 filters, 3x3 size), 2 max-pooling layers (2x2 size), 2 hidden layers (size 256), and a dropout value of 0.5.  
