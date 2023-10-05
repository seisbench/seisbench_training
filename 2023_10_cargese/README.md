# SeisBench training - Cargèse October 2023

Welcome to the SeisBench training at the Cargèse subduction school 2023!
This training is not linearly but offers different routes, depending on what you want to try.
Each route consists of a set of Colab notebooks that should be followed in order.
The routes are (mostly) independent of each other.

Once you've finished the routes you are interested in (or if you are already an experienced user),
you can try out the exercises. The exercises are open-ended tasks to get to know the particularities
of deep learning based models. They are intended to serve as a starting point for discussion. 

If you need any help, check out the [SeisBench repository](https://github.com/seisbench/seisbench),
the [SeisBench documentation](https://seisbench.readthedocs.org/), or ask the instructors.

To run these examples locally, you will need a local installation of SeisBench.
Follow the instructions in the SeisBench repository or documentation for installation.
The tutorial notebooks can be downloaded from the repository.

## Recommended routes

I want to learn how to train a model:

1. Dataset basics [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/01a_dataset_basics.ipynb)
2. Model API [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/01b_model_api.ipynb)
3. Generator pipelines [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/01c_generator_pipelines.ipynb)
4. Training PhaseNet [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/03a_training_phasenet.ipynb)

I want to build an earthquake catalog:

1. Model API [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/01b_model_api.ipynb)
2. Building an event catalog [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/03c_catalog_seisbench_gamma.ipynb)

I want to compile a new training dataset:

1. Dataset basics [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/01a_dataset_basics.ipynb)
2. Creating a dataset [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/03b_creating_a_dataset.ipynb)

Miscellaneous:

- Comparing seismic pickers [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/02a_deploy_model_on_streams_example.ipynb)
- Denoising waveforms with DeepDenoiser [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/02b_deep_denoiser.ipynb)
- Picking depth phases and identifying earthquake depth [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench/blob/main/examples/02c_depth_phases.ipynb)
- Building a catalog from OBS data [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench_training/blob/main/2023_07_13_obs_workshop.ipynb) 

## Exercises

Exercise notebook template: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seisbench/seisbench_training/blob/main/2023_10_cargese/exercise_template.ipynb)

**Finding picker inconsistencies:** Traditional seismic phase pickers have certain symmetries,
e.g., they are invariant to time shifts of the input or to rotations around the Z axis.
Deep learning pickers do not come with these guarantees. Load a picker and download a few
waveforms and start figuring out, how these inconsistencies affect predictions. Try shifting the
input by a few samples or rotating the traces. Which models and weights are more or less affected?
Play with the `overlap` parameter to see how consistency and run time trade off against each other.

**Comparing earthquake catalogs:** With several pickers and even more sets of weights available,
it is not apparent which one is most suitable for a given region. Build multiple catalogs and
compare them. Which pickers find more events? For which picker can a higher fraction of picks
be associated? Do different pickers find the same events? And do different pickers maybe event
produce the same false positives?

**Transfer-train a picker:** For small datasets, often the best way for training a model is not
to start for scratch, i.e., a random initialisation, but to start from a model trained on a much larger
dataset. This is called transfer learning. Starting from the "Training PhaseNet" example, transfer-train
a picker. Maybe try it on even shorter parts of the ETHZ dataset. How does your transfer-trained picker
differ from a directly trained one?

**Build your own model:** *(Requires prior deep learning experience)*
SeisBench is a flexible library and the datasets have many annotations not used
in the current model. So why not train your own model? Maybe estimate magnitude,
distance to the event, build another picker, ... .