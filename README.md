# CIFAR-10H

CIFAR-10H is a new dataset of soft labels reflecting human perceptual uncertainty for the 10,000-image [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html) test set, first appearing in the paper:

[Joshua C. Peterson](https://twitter.com/joshuacpeterson)\*, [Ruairidh M. Battleday](https://ruairidh.mycpanel.princeton.edu/)\*, [Thomas L. Griffiths](http://cocosci.princeton.edu/tom/index.php), & [Olga Russakovsky](https://www.cs.princeton.edu/~olgarus/) (2019). Human uncertainty makes classification more robust.
*In Proceedings of the IEEE International Conference on Computer Vision.* ([preprint](https://arxiv.org/abs/1908.07086))

And more recently in:

[Ruairidh M. Battleday](https://ruairidh.mycpanel.princeton.edu/)\*, [Joshua C. Peterson](https://twitter.com/joshuacpeterson)\*, & [Thomas L. Griffiths](http://cocosci.princeton.edu/tom/index.php) (2020). Capturing human categorization of natural images by combining deep networks and cognitive models. ([preprint](https://arxiv.org/abs/1904.12690))

And:

Pulkit Singh, Peterson, [Joshua C. Peterson](https://twitter.com/joshuacpeterson), [Ruairidh M. Battleday](https://ruairidh.mycpanel.princeton.edu/), & [Thomas L. Griffiths](http://cocosci.princeton.edu/tom/index.php) (2020). End-to-end deep prototype and exemplar models for predicting human behavior. Proceedings of the 42nd Annual Conference of the Cognitive Science Society. ([preprint](https://arxiv.org/abs/2007.08723))

#### Repository Contents

`data/cifar10h-counts.npy` - `10000 x 10` numpy matrix containing human classification counts (out of ~50) for each image and class.

`data/cifar10h-probs.npy` - `10000 x 10` numpy matrix containing normalized human classification counts (probabilities) for each image and class. These are the labels used for training and evaluation in the above paper.

The order of the 10,000 labels matches the original CIFAR-10 test set order.

`data/cifar10h-raw.zip` - Zip archive containing `cifar10h-raw.csv`, raw, annotator-level data. The columns are as follows:

* `annotator_id` is a unique integer ID (starting at 0) for the annotator from Amazon Turk (but is not their Worker ID). For each ID, there are 210 associated ratings trials (10 attention checks + 200 normal trials).
* `trial_index` indexes the trial for each subject, from 0 to 219. The was cleaned up to not count the fixation click jspsych trials nor count practice trials which may vary in amount across participants.
* `is_attn_check` is 0 for normal trials and 1 for attention checks
* `true_category` is the true string class name (e.g., "cat") of the image
* `chosen_category` is the string class name (e.g., "cat") chosen by the annotator for the image
* `true_label` is the true integer class label of the image
* `chosen_label` the integer class label chosen by the annotator for the image
* `correct_guess` whether the guess was correct (i.e., when true_label==chosen_label), marked by 1, or 0 otherwise
* `cifar10_test_set_idx` is the index of the image in the original CIFAR-10 test set. Attention check trials are marked -99999 to prevent people from indexing the last image of the dataset by accident when using python. 
* `image_filename` is the filename of the PNG filename for the stimulus
* `subcategory` shows the subordinate class label, which we've never used before, but which is recoverable from the image filenames and may be useful in the future.
* `reaction_time` how long in milliseconds taken by the annotator to provide a response for the current trial
* `time_elapsed` gives milliseconds passed at the end of each trial. The first is equal to the rt for the first trial. The rest are essentially cumulative rt values.

The mapping from category names to labels is: "airplane": 0, "automobile": 1, "bird": 2, "cat": 3, "deer": 4, "dog": 5, "frog": 6, "horse": 7, "ship": 8, "truck": 9, which match the original CIFAR-10 dataset.


#### TODO

* Dataset statistics / summary
* Keras loading example
* PyTorch loading example
* Classifier evaluation comparison table
* Example training scripts

#### References

Krizhevsky, A., & Hinton, G. (2009). Learning multiple layers of features from tiny images (Vol. 1, No. 4, p. 7). Technical report, University of Toronto. ([website](https://www.cs.toronto.edu/~kriz/cifar.html))
