## Classify the Roman ruler on a coin based on the coin's description

Data was taken from eBay _Ancient Roman Coin_ listings.
Some of them are tagged with the aspect of a Ruler and some are not. 
For future usage I needed to fill the gaps for the entries that do not have the ruler specified.

Using CNN classification I was able to reach 95% accuracy.

Based on https://github.com/jiegzhan/multi-class-text-classification-cnn

### Why Neural Networks?

From most entries you could deduct the ruler by a simple RegEx. Problem comes with ±10% of the 
entries where the names are not included in the description at the expected format 

For example the entry 'FL IVL CONSTANTIVS NOB C - GLORIA EXERCITVS 334-335 AD' stands for 
_Constantine II_. No reasonable RegEx could deudct that, but the CNN had no problem.

### Data: 

 - Input: **description**

    - Example: "FL IVL CONSTANTIUS NOB C - GLORIA EXERCITVS 334-335 AD"
    
 - Output: **ruler**

     - Example: Constantine II

### Train:

 - Command: python3 train.py training_data.file parameters.json
 - Example: ```python3 train.py ./data/title_ruler.csv ./parameters.json```
 
 A directory will be created during training, and the trained model will be saved in this directory. 

### Predict:

 Provide the model directory (created when running ```train.py```) and new data to ```predict.py```.
 - Command: python3 predict.py ./trained_model_directory/ new_data.file
 - Example: ```python3 predict.py ./trained_model_1521137138/ ./data/small_samples.json```

### Reference:
 - [Implement a cnn for text classification in tensorflow](http://www.wildml.com/2015/12/implementing-a-cnn-for-text-classification-in-tensorflow/)
