# CIFAR-10H

CIFAR-10H is a new dataset of soft labels reflecting human perceptual uncertainty for the 10,000-image [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html) test set, first appearing in the paper:

[Joshua C. Peterson](https://twitter.com/joshuacpeterson)\*, [Ruairidh M. Battleday](https://ruairidh.mycpanel.princeton.edu/publications/)\*, [Thomas L. Griffiths](http://cocosci.princeton.edu/tom/index.php), & [Olga Russakovsky](https://www.cs.princeton.edu/~olgarus/) (2019). Human uncertainty makes classification more robust.
*In Proceedings of the IEEE International Conference on Computer Vision.*

#### Repository Contents

`data/cifar10h-counts.npy` - `10000 x 10` numpy matrix containing human classification counts (out of ~50) for each image and class.

`data/cifar10h-probs.npy` - `10000 x 10` numpy matrix containing normalized human classification counts (probabilities) for each image and class. These are the labels used for training and evaluation in the above paper.

#### TODO

* Dataset statistics / summary
* Keras loading example
* PyTorch loading example
* Classifier evaluation comparison table
* Example training scripts

#### References

Krizhevsky, A., & Hinton, G. (2009). Learning multiple layers of features from tiny images (Vol. 1, No. 4, p. 7). Technical report, University of Toronto.
