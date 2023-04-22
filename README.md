# Digitization of ICAL output data and labelling
This code uses the output file achieved from simulation of INO-ICAL detector.The output files can be found in https://github.com/Hemalatanayak/ical_g4/tree/master/data . All the input files are digitized and then concatenated.Refer to **digitization.ipynb** to digitize and **labeling.ipynb** to concatenate and label.

Digitization of data is important because it contains all the information needed for a precise measurement and easy to debug the system. For digitization, we need to know the total no. of strips and layers in a detector.

- Generally, Dimension of a RPC = 2m x 2m
- No. of strips in one RPC = 64
- Dimension of ICAL geometry used in our simulation = 16m x 16m
- Total no. of strips = 64 x 8 = 512 (to digitize x and y values)
- Total no. of glass layers = 150 (to digitize z values )

After digitizing the data we have added graphID,graph labels and nodeID in the file named **labeled_data.csv**. Where,

- graphLabel = Energy of the particle
- graphID = combination of graphlabel and eventID.
- nodeID = unique for each set of ( x_dig, y_dig, z_dig ) values.

This labeled_data.csv will be used to make graph type data structure using dgl library and then GNN will be applied.
# Graph data structure
A graph is a type of non-linear data structure made up of vertices and edges. Vertices are also known as nodes, while edges are lines or arcs that link any two nodes in the network.

To construct the graph, refer **graph.ipynb** . In our constructed graph ;

- Node feature = Digitized hit coordinates ( x , y, z )
- Edge feature = Time difference( t )

**Note: Few files are removed due to file size limitations in GitHub (labeled_data.csv, saved_graphs.zip)**