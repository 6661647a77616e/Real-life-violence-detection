
# Real-life-violence-detection

start jupyter notebook using uv 
<code>uv run --with jupyter jupyter lab</code>

install dependencies with 
<code>uv pip install -r requirements.txt</code>

incase you want to add new dependencies dont use !pip install [dep] in jupyter notebook, instead installed it manually and start the jupyter notebook again

## Data Collection

The data used was data provided by Kaggle. The data is largely divided into Violence and NonViolence for 1000 images each.

[Real Life Violence Situations Data](https://www.kaggle.com/mohamedmustafa/real-life-violence-situations-dataset)

## The code was based on 
[Real Life Voilence Detection using Inceptionv3](https://www.kaggle.com/code/nandinibagga/real-life-violence-detection-using-inceptionv3)

## Model
I have used `InceptionV3` which is a pretrained Imagenet CNN model provided by `Keras`.

Update - `MobileNetV2` is used to with improved accuracy and predictions. This model was created on Kaggle. 

![image](images/graph.PNG)

## Output
Output is in the form of a video, which will tell violence/ non-violence on the top left corner.

However my machine and kaggle option is not suffice so i stop at 

```python
# Train the head of the network for a few epochs (all other layers are frozen)
# This allows the new FC layers to start learning meaningful patterns instead of random values
print('-' * 100)
print("[INFO] Training head...")
print('-' * 100)

H = model.fit(
    trainAug.flow(trainX, trainY, batch_size=32),
    steps_per_epoch=len(trainX) // 32,
    validation_data=valAug.flow(testX, testY, batch_size=32),
    validation_steps=len(testX) // 32,
    epochs=args["epochs"]
)
```


![v_output](https://user-images.githubusercontent.com/56165694/123710940-366c7d00-d88d-11eb-866e-c09e2185c571.gif)



## Reference
https://www.pyimagesearch.com/2019/07/15/video-classification-with-keras-and-deep-learning/
https://www.pyimagesearch.com/2019/06/03/fine-tuning-with-keras-and-deep-learning/
