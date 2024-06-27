# algoproject
Hi everyone,  I'm currently working on a project where I need to load a TensorFlow SavedModel and use it with a custom input layer in Keras. However, I'm running into issues when trying to perform inference with the model.








---

Title: Trouble Loading and Using a TensorFlow SavedModel with Custom Input Layer in Keras

Body:

Hi everyone,

I'm currently working on a project where I need to load a TensorFlow SavedModel and use it with a custom input layer in Keras. However, I'm running into issues when trying to perform inference with the model. Here’s what I’ve done so far:

1. Loaded the SavedModel as an inference-only layer:
   
    import tensorflow as tf
    from keras.layers import TFSMLayer
    from keras import Input
    from keras.models import Model

    base_model = TFSMLayer("path/to/savedmodel", call_endpoint='serving_default')

    input_layer = Input(shape=(32,), dtype='float64')

    output_layer = base_model(input_layer)

    model = Model(inputs=input_layer, outputs=output_layer)
    
2. Converted test data to the required float64 dtype:
   
    import pandas as pd

    test_data = pd.read_csv("path/to/testdata.csv")
    test_data_float64 = tf.cast(test_data.values, tf.float64)
    
3. Attempted to use the model for inference:
   
    predictions = model(test_data_float64)
    
However, I’m encountering issues with the input data type and shape compatibility. 

### My Questions:

1. Data Type Compatibility: How can I ensure that the input data is correctly formatted and compatible with the expected input dtype of the TFSMLayer?
2. Shape Issues: Are there any common pitfalls or best practices when dealing with custom input layers in Keras models that load TensorFlow SavedModels?
3. Inference with Custom Layers: Is there a better approach to modify the input layer of a pre-trained TensorFlow SavedModel for inference in Keras?

Any guidance or suggestions on how to resolve these issues would be greatly appreciated. Thank you!

---

Feel free to post this question on GitHub, and it should be ready for others to understand and provide help without any proprietary information being leaked.
