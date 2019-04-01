~~This project is ongoing and uncompleted now.:blush: (2019.3.30)~~
This project is ongoing and uncompleted now.:dizzy_face: (2019.4.1)
***

This is the project page for our paper:

"Towards Visual Feature Translation." Hu, J., Ji, R., Liu, H., Zhang, S., Deng, C., & Tian, Q. In *CVPR 2019.* \[[paper](https://arxiv.org/abs/1812.00573)\]

If you have any problem, please feel free to contact us.

![The framework of our paper.](https://github.com/hujiecpp/VisualFeatureTranslation/blob/master/Figures/Framework.png)
# 1. Feature Extraction

This section contains the process of collecting popular content-based image retrieval features for preparing the meta-data of our paper.

The extracted features are evaluated in this section.

## 1.1. Evaluation
### Datasets
Datasets for evaluation:  
- [Holidays](http://lear.inrialpes.fr/people/jegou/data.php#holidays) [1]
- [Oxford5k](http://www.robots.ox.ac.uk/~vgg/data/oxbuildings/) [2]
- [Paris6k](http://www.robots.ox.ac.uk/~vgg/data/parisbuildings/) [3]

Dataset for PCA whitening and creating codebooks:
- [Google-Landmarks](https://www.kaggle.com/c/landmark-retrieval-challenge) [4]

### Measurement
We use the mean Average Precision (mAP) provided by the official site of above datasets for evaluation.

The details can be found in: `./Extraction/`

## 1.2. Features
Please note that our extractions for images do not use the bounding boxes of the objects.

The local features (e.g., SIFT and DELF) are aggregated by the codebooks learned on 4,000 randomly picked images of Google-Landmarks dataset.

And the features of picked images are used to train the PCA whitening for all features of other images.

The features are listed bellow, and the details can be found in: `./Extraction/`

- **SIFT-FV** and **SIFT-VLAD**: The Scale Invariant Feature Transform (SIFT) [5] features are extracted and then aggregate by Fisher Vector (FV) [6] and Vector of Locally Aggregated Descriptors (VLAD) [7].

- **DELF-FV** and **DELV-VLAD**: The DEep Local Features (DELF) [8] are extracted and then aggregate also by FV and VLAD.

- **V-CroW** and **R-CroW**: The abbreviation V represents the VGG [9] backbone network, and R [10] represents the Resnet50 backbone network. The Cross-dimensional Weighting (CroW) [11] are then used to aggregate the deep features generated by the backbone networks.

- **V-SPoC** and **R-SPoC**: The Sum-Pooled Convolutional features (SPoC) [12] are used to aggregate the deep features generated by the backbone networks.

- **V-MAC**, **V-rMAC** and **R-MAC**, **R-rMAC**: The Maximum Activations of Convolutions (MAC) [13] and the regional Maximum Activations of Convolutions (rMAC) [14] are used to aggregate the deep features generated by the backbone networks.

- **V-GeM**, **V-rGeM** and **R-GeM**, **R-rGeM**: The Generalized-Mean pooling (GeM) [15] is used to aggregate the deep features generated by the backbone networks.

## 1.3. Results
The mAP (%) of collected features are as follows:

|          | Holidays | Oxford5k | Paris6k |
|   :---:  |:--------:|:--------:|:-------:|
|SIFT-FV   |61.77     |36.25     |36.91    |
|SIFT-VLAD |63.92     |40.49     |41.49    |
|DELF-FV   |83.42     |73.38     |83.06    |
|DELF-VLAD |84.61     |75.31     |82.54    |
|V-CroW    |83.17     |68.38     |79.79    |
|V-GeM     |84.57     |82.71     |86.85    |
|V-MAC     |74.18     |60.97     |72.65    |
|V-rGeM    |85.06     |82.30     |87.33    |
|V-rMAC    |83.50     |70.84     |83.54    |
|V-SPoC    |83.38     |66.43     |78.47    |
|R-CroW    |86.38     |61.73     |75.46    |
|R-GeM     |89.08     |84.47     |91.87    |
|R-MAC     |88.53     |60.82     |77.74    |
|R-rGeM    |89.32     |84.60     |91.90    |
|R-rMAC    |89.08     |68.46     |83.00    |
|R-SPoC    |86.57     |62.36     |76.75    |

# 2. Feature Translation

To do.
`./Translation/`

# 3. Relation Mining

To do.
`./Relation/`

# 4. Reference
[1] "Hamming embedding and weak geometric consistency for large scale image search." Jegou, H., Douze, M., & Schmid, C. In *ECCV 2008.*  
[2] "Object retrieval with large vocabularies and fast spatial matching." Philbin, J., Chum, O., Isard, M., Sivic, J. & Zisserman, A. In *CVPR 2007.*  
[3] "Lost in Quantization: Improving Particular Object Retrieval in Large Scale Image Databases." Philbin, J., Chum, O., Isard, M., Sivic, J. & Zisserman, A. In *CVPR 2008.*  
[4] "Large-scale image retrieval with attentive deep local features." Noh, H., Araujo, A., Sim, J., Weyand, T., & Han, B. In *ICCV 2017.*  
[5] "Distinctive image features from scale-invariant keypoints." Lowe, D. G. *IJCV 2004.*  
[6] "Large-scale image retrieval with compressed fisher vectors." Perronnin, F., Liu, Y., Sánchez, J., & Poirier, H. In *CVPR 2010.*  
[7] "Aggregating local descriptors into a compact image representation." Jégou, H., Douze, M., Schmid, C., & Pérez, P. In *CVPR 2010.*  
[8] "Large-scale image retrieval with attentive deep local features." Noh, H., Araujo, A., Sim, J., Weyand, T., & Han, B. In *ICCV 2017.*  
[9] "Very deep convolutional networks for large-scale image recognition." Simonyan, K., & Zisserman, A. *arXiv:1409.1556.*  
[10] "Deep residual learning for image recognition." He, K., Zhang, X., Ren, S., & Sun, J. In *CVPR 2016.*  
[11] "Cross-dimensional weighting for aggregated deep convolutional features." Kalantidis, Y., Mellina, C., & Osindero, S. In *ECCV 2016.*  
[12] "Aggregating local deep features for image retrieval." Babenko, A., & Lempitsky, V. In *ICCV 2015.*  
[13] "Visual instance retrieval with deep convolutional networks." Razavian, A. S., Sullivan, J., Carlsson, S., & Maki, A. *MTA 2016.*  
[14] "Particular object retrieval with integral max-pooling of CNN activations." Tolias, G., Sicre, R., & Jégou, H. In *ICLR 2016.*  
[15] "Fine-tuning CNN image retrieval with no human annotation." Radenović, F., Tolias, G., & Chum, O. *PAMI 2018.*  
