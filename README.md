## Graph Reduced Order Models ##

In this repository we implement reduced order models for cardiovascular simulations using Graph Neural Networks (GNNs).

### Install the virtual environment ###

Let us first install `virtualenv`:

    pip install virtualenv

Then, from the root of the project:

    bash create_venv.sh

This will create a virtual environment `gromenv` following python packages: matplotlib, vtk, scipy, dgl, torch, sigopt.

### Download the data ###

To download the data, simply type

    bash download_data.sh

in the root directory. This will automatically generate a directory `graphs/vtps` containing the dataset in `vtp` format. To inspect these files, use for example [Paraview](https://www.paraview.org)

### Generate a graph ###

Within the directory `graphs`, type

    python generate_graph.py $MODELNAME.vtp $MODELNAME.grph

For example,

    python generate_graph.py 0063_1001 0063_1001.grph

The graph will be saved in `graphs/data`.

### Train a GNN ###

Within the directory `graphs`, type

    python training.py $MODELNAME

For example,

    python training.py 0063_1001

The parameters of the trained model and hyperparameters will be saved in `network/models`, in a folder named as the date and time when the training was launched.

### Test a GNN ###

Within the directory `graphs`, type

    python tester.py $MODELNAME $NETWORKPATH

For example,

    python tester.py 0063_1001 models/01.01.1990_00.00.00

This will save comparative plots in the same directory.
In the example, `models/01.01.1990_00.00.00` is a model generated after training (see Train a GNN).
