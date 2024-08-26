## Google Summer Of Code 2024_INCF
Repository for the details of my work in the Google Summer Of Code 2024 with the INCF organisation 

**Mentee:**       [Aditya Pandey](https://github.com/AdityaBITMESRA)<br/>
**Mentors:**      [Ankur Sinha](https://github.com/sanjayankur31), [Padraig Gleeson](https://github.com/pgleeson)<br/>
**Organization:** [INCF](https://incf.org/)<br/>
**Project Name:** Implementation of SWC to NeuroML converter in PyNeuroML<br/>

This readme file will contain details about my work that I have done throughout my GSoC period with the INCF organisation.
I have also blogged about my journey and challenges in my personal blog here 
[Aditya's Blog](https://adityabitmesra.github.io/personalblog/)

## Project Overview

My goal was to make a Python Based SWC to NeuroML Converter.
With the instruction from my mentors I divided my task into two parts which was trying to make a Python program to Load the 
SWC format and then a second one to do the conversion.

The converter was tested against many SWC files from [Neuromorpho.org](https://neuromorpho.org/) and some major cells from [Allen 
Institute database](https://github.com/OpenSourceBrain/AllenInstituteNeuroML/tree/master/CellTypesDatabase/models)


## **SWC to NeuroML Converter: Development and Testing**


The first step was to make a SWC loader file.
This [loader file](https://github.com/NeuroML/pyNeuroML/blob/development/pyneuroml/swc/LoadSWC.py) is a Python module designed to 
handle SWC files, which are commonly used to represent neuronal morphology data. Here are the key components of the loader:

## SWC to NeuroML Converter Components

### 1. SWC Loader Module

#### SWCNode Class
- Represents individual nodes in the SWC file
- Stores: node ID, type, 3D coordinates, radius, parent ID
- Defines constants for node types (e.g., SOMA, AXON, BASAL_DENDRITE)

#### SWCGraph Class
- Represents the entire SWC structure as a graph
- Maintains a list of SWCNode objects
- Key methods:
  1. Add nodes to the graph
  2. Retrieve nodes by ID or type
  3. Find parent and child nodes
  4. Identify branch points and nodes with multiple children
  5. Export the graph back to an SWC file

#### load_swc Function
- Reads SWC file and creates an SWCGraph object
- Parses header information and node data
- Manages potential errors in the file format

#### Utility Functions
- Includes `parse_header` for specific SWC file aspects
- Implements error handling and logging for debugging

### 2. NeuroML Export Module

#### NeuroMLWriter Class
- Converts SWC graph data to NeuroML format
- Handles different neuron segment types
- Creates appropriate segment groups

#### Key Features
1. **Soma Handling**: Implements NeuroMorpho.Org v5.3 guidelines
   - Supports single contour, multiple contours, single point representations
2. **Segment Grouping**: Creates groups for soma, axon, dendrites
   - Handles unbranched segment group creation
3. **Metadata Preservation**: Retains original SWC file metadata
4. **Error Handling & Logging**: Ensures reliable conversion and aids debugging

### 3. Comprehensive Testing

#### SWC Loader Test Suite
1. Initialization and representation of SWC nodes
2. SWCGraph operations (adding nodes, retrieving, filtering)
3. Metadata handling and duplicate ID prevention
4. Load-export-compare for file reading/writing accuracy

#### NeuroML Export Test Suite
1. SWC string parsing and NeuroML conversion validation
2. Checks for NeuroML elements, segments, groups, coordinates
3. Error handling verification
4. Special soma case testing

#### Testing Methodology
- Uses temporary files for SWC parsing tests
- Validates against real-world data from Neuromorpho.org and Allen Institute

<h2>Merged Pull Requests</h2>

<p> Here's a list of significant PRs that have been merged:</p>

<ol>
  <li><a href="https://github.com/NeuroML/pyNeuroML/pull/384"><span style="color: #0366d6;">Initial implementation of SWC loader</span></a>
    <ul>
      <li>Added SWCNode and SWCGraph classes</li>
      <li>Implemented basic file parsing functionality</li>
    </ul>
  </li>

  <li><a href="https://github.com/NeuroML/pyNeuroML/pull/404"><span style="color: #28a745;">SWC export module and test module</span></a>
    <ul>
      <li>Adds function to export SWC graph to a new SWC file</li>
      <li>2.Adds tests to verify if generated file and input file are similar</li>
    </ul>
  </li>
