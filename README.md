# GSoC2024_INCF
Repository for the details of my work in the Google Summer Of Code 2024 with the INCF organisation 

This readme file will contain details about my work that I have done throughout my GSoC period with the INCF organisation.
I have also blogged about my journey and challenges in my personal blog here 
[Aditya's Blog](https://adityabitmesra.github.io/personalblog/)

My goal was to make a Python Based SWC to NeuroML Converter.
With the instruction from my mentors I divided my task into two parts which was trying to make a Python program to Load the 
SWC format and then a second one to do the conversion.

The converter was tested against many SWC files from [Neuromorpho.org](https://neuromorpho.org/) and some major cells from [Allen 
Institute database](https://github.com/OpenSourceBrain/AllenInstituteNeuroML/tree/master/CellTypesDatabase/models)

The first step was to make a SWC loader file.
This loader file is a Python module designed to handle SWC (Standardized Morphology Data Format) files, which are commonly used 
to represent neuronal morphology data. Here are the key components of the loader:

SWCNode class: This class represents individual nodes in the SWC file. It stores information such as node ID, type, 3D coordinates, 
radius, and parent ID. It also defines constants for different node types (e.g., SOMA, AXON, BASAL_DENDRITE).
SWCGraph class: This class represents the entire SWC structure as a graph. It maintains a list of SWCNode objects and provides methods to:

1. Add nodes to the graph
2. Retrieve nodes by ID or type
3. Find parent and child nodes
4. Identify branch points and nodes with multiple children
5. Export the graph back to an SWC file


load_swc function: This function reads an SWC file and creates an SWCGraph object. It handles parsing of both header information and node 
data, while also managing potential errors in the file format.

Utility functions: The module includes additional functions like parse_header to handle specific aspects of the SWC file format.
Error handling and logging: The loader implements robust error checking and uses Python's logging module for debugging and error reporting.

