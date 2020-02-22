# Unsupervised ML with Keras pre-trained models and t-SNE
This project allows images to be automatically grouped into like clusters using a combination of machine learning techniques.

First, pre-trained deep learning models are used to obtain feature vectors for the images.

Then, k-means is ran on these feature-vectors.

## extract.py
Uses one of the [pre-trained deep learning models avaliable in Keras](https://keras.io/applications) to extract a feature vector for all images in a source directory.

I used the following guide to [install Keras with TensorFlow](https://keras.io/#installation) using conda.

The script expects as an argument the path to a tab separated file that has at a minimum a column called 'id' and another called 'image' which contains the file name. The images **need** to be located in a directory called **images** which is located in the same directory as the source file.

For example if a file called example.tsv contains a single record:

| id | image |
| -- |:-----:|
| 1  | 1.jpg |

Then it would have the following directory structure:
```
.
+-- example.tsv
+-- images
|   +-- 1.jpg
```

The results are saved to a tab separated file postfixed with '_features.

## cluster.py
Now, just run cluster.py to get a folder of clusters using k-means, trained on the feature vectors. The cluster amount is the only argument that needs to be specified.
