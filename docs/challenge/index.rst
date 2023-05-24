ICML 2023 Topological Deep Learning Challenge
=====================
Welcome to the ICML 2023 Topological Deep Learning Challenge, hosted by the second annual `Topology and Geometry (TAG) in Machine Learning Workshop <https://www.tagds.com/events/conference-workshops/tag-ml23>`_ at ICML. 

Lead organizers: Mathilde Papillon, Dr. Tegan Emerson, Dr. Henry Kvinge, Dr. Tim Doster, Dr. Bastian Rieck, Dr. Sophia Sanborn and Dr. Nina Miolane.


Description of the Challenge
-------------

The purpose of this challenge is to foster reproducible reasearch in Topological Deep Learning, by crowdsourcing the open-source implementation of neural networks on topological domains. Participants are asked to contribute code for a previously existing Topological Neural Network (TNN), and test it on a toy dataset. 

Implementations are built using TopoModelX, a Python package for deep learning on topological domains. Each submission takes the form of a Python script defining a layer of a given TNN, and a Jupyter Notebook implementing and testing a TNN built with this layer. The TNN layer leverages the coding infrastructure and building blocks from the package `TopoModelX <https://github.com/pyt-team/TopoModelX/tree/main/topomodelx>`_. Participants submit their Python script and Jupyter Notebook via `Pull Requests <https://github.com/pyt-team/TopoModelX/pulls>`_ to this GitHub repository, see Guidelines below.

*Note:* *We invite participants to review this file regularly, as details are added to the guidelines when questions are submitted to the organizers.*

⭐️ Publication Outcomes for Participants ⭐️
-------------
**Every submission respecting the submission requirements** will be included in a white paper summarizing findings of the challenge. Participants will have the opportunity to co-author this publication.

Participants with the top 8 best submissions will have the opportunity to co-author a software paper on TopoModelX submitted to the **Journal of Machine Learning Research**.

🏆 The best submisison in every topoglogical domain (hypergraph, simplcial, cellular, combinatorial) will recieve special recognition at the  `TAG in Machine Learning Workshop <https://www.tagds.com/events/conference-workshops/tag-ml23>`_ at ICML. 


Deadline
-------------
The final Pull Request submission date and time must take place before **July 13, 2023 at 16:59 (Pacific Standard Time)**.
Participants are welcome to modify their Pull Request until this time.

How to Submit
-------------
Everyone can participate and participation is free. It is sufficient to:

- send a Pull Request
- respect Submission Requirements.

An acceptable Pull Request automatically subscribes a participant/team to the challenge.

Guidelines
-------------
We encourage the participants to start submitting their Pull Request early on. This allows to debug the tests and helps to address potential issues with the code.

In the case of multiple submissions implementing the same model, earlier Pull Requests will be given priority consideration.

Teams are accepted and there is no restriction on the number of team members.

There is no restriction on the amount of submisisons (Pull Requests) per participant/team. One model per Pull Request.

The principal developpers of TopoModelX are not allowed to participate.

Submission Requirements
-------------
The submisison must implement a pre-exisitng model from the literature included in Fig. 11 of the review `Architectures of Topological Deep Learning: A Survey of Topological Neural Networks <https://arxiv.org/pdf/2304.10031.pdf>`_.

All submitted code complies with TopoModelX's GitHub Action workflow, successfully passing all tests, linting, and formatting (e.g., Black, isort, flake8).

The Pull Request contains three new files:

1. {name of model}_layer.py (ex.: hsn_layer.py) :

- stored in the directory topomodelx/nn/{domain of model}, where {domain of model} is simplicial, cellular, or hypergraph.
- contains one class, {Name of model}Layer (ex.: HSNLayer), which uses TopoModelX computational primitives to implement one layer of the model. One layer is equivalent to the message passing depicted in the tensor diagram representation fo the model (Fig. 11, Architectures of Topological Deep Learning).
- examples are provided in topomodelx/nn/simplicial and topomodelx/nn/cellular. 

2. {name of model}_train.ipynb (ex.: hsn_train.ipynb) :

- stored in the directory tutorials/ and contains the following steps:

  1. Pre-processing
        - imports necessary packages as well as {Name of model}Layer class
        - loads the protein-protein-interaction graph `using TopoNetX <https://github.com/pyt-team/TopoNetX/blob/71e840ea5a475027ca9b4231563834547463cf19/toponetx/datasets/utils.py#LL9C6-L9C6>`_ and assigns labels.
        - lifts the graph into the domain of choice (hypergraph, simplicial complex, celular complex, combinatorial complex) using TopoNetX.
  
  2. Creating the neural network
        - defines a class {Name of model} (ex.: HSN) that inherits from torch.nn.Module and uses {Name of model}Layer along with torch.Linear layers to create a Topological Neural Network.
  
  3. Training the neural network on a classification task
        - defines a simple training loop for node/edge/complex classification (depending on which features the model outputs).
        - note: submissions are not evaluated based on model performance, but rather code quality and accuracy of model implementation.
- examples are provided in tutorials/
  
  3. test_{name_of_model}_layer.py (ex.: test_hsn_layer.py)
  
  - stored in directory test/nn/{domain of model}
  - contains one class, Test{Name of model}Layer (ex.: TestHSNLayer), which contains unit tests for all of the functions contianed in the {Name of model}Layer class. Please use pytest (not unittest).
  - examples are provided in test/nn/simplicial and test/nn/cellular.
  
  **Note :** in the case that your {Name of model}Layer requires further manipulation of the computational primitives in topomodelx/base, you may include modifications to the files in topomodelx/base or new files. Every single new function MUST be accompanied by a new unit test stored in an appropriately named/located test file. With that being said, we highly encourage participants to value simplicity and make the most of the computational primitives as is.
  
Evaluation
-------------

The `Condorcet method <https://en.wikipedia.org/wiki/Condorcet_method>`_ will be used to rank the submissions and decide on the winners. The evaluation criteria will be:

- Does the submission implement the chosen model correctly, specifically in terms of its message passing scheme? (The training schemes do not need to match that of the original model).
- How readable/clean is the implementation? How well does the submission respect TopoModelX's APIs?
- Is the submission well-written? Do the docstrings help understand the methods? Are the unit tests robust?

Note that these criteria do not reward model performance, nor complexity of training. Rather, the goal is to implement well-written and accurate model architectures that will foster reproducible research in our field.

Selected TopoModelX maintainers and collaborators, as well as each team whose submission(s) respect(s) the guidelines, will vote once on Google Form to express their preference for the best submission in every topological domain. Note that each team gets only one vote, even if there are several participants in the team.

The 3 preferences must all be distinct: e.g. one cannot select the same submission for both first and second place. Such irregular votes will be discarded. A link to a Google Form will be provided to record the votes. It will be required to insert an email address to identify the voter. The voters will remain secret--only the final ranking will be published.
