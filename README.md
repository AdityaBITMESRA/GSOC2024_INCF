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
## SWC to NeuroML Converter: Development and Testing

### 1. SWC Loader Module
- **SWCNode Class**: Represents individual nodes (ID, type, coordinates, radius, parent ID)
- **SWCGraph Class**: Represents entire SWC structure, with methods for node manipulation
- **load_swc Function**: Reads SWC file, creates SWCGraph object
- **Utility Functions**: Parsing headers, error handling, logging

### 2. NeuroML Export Module
- **NeuroMLWriter Class**: Converts SWC graph to NeuroML format
- **Key Features**:
  1. Soma handling (NeuroMorpho.Org v5.3 guidelines)
  2. Segment grouping (soma, axon, dendrites)
  3. Metadata preservation
  4. Error handling & logging

### 3. Testing
- **SWC Loader**: Node initialization, graph operations, metadata handling
- **NeuroML Export**: Conversion validation, element checks, error handling
- **Methodology**: Temporary file usage, real-world data validation

[Link to SWC loader file](https://github.com/NeuroML/pyNeuroML/blob/development/pyneuroml/swc/LoadSWC.py)
<h2>Pull Requests</h2>

<h3 style="color: #0366d6;">Merged Pull Requests</h3>

<p>Here's a list of significant PRs that have been merged:</p>

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
      <li>Adds tests to verify if generated file and input file are similar</li>
    </ul>
  </li>
</ol>

<h3 style="color: #f9c513;">Significant Pull Request Awaiting Approval</h3>

<div style="border-left: 4px solid #f9c513; padding-left: 20px;">
  <h4><a href="https://github.com/NeuroML/pyNeuroML/pull/407"><span style="color: #e36209;">NeuroML Export Module Implementation</span></a></h4>
  <p>This crucial PR introduces the core functionality for converting SWC to NeuroML format. It is currently under review and pending approval.</p>
  <ul>
    <li>Adds ExportNML module which creates NeuroML files</li>
    <li>Adds test module which tests for Soma handling cases</li>
    <li>Implements NeuroMLWriter class for SWC to NeuroML conversion</li>
    <li>Handles different neuron segment types and creates appropriate segment groups</li>
  </ul>
  <p><strong>Status:</strong>Approved(with some major tweaks from my mentor)<a href ="https://github.com/sanjayankur31">Ankur Sinha</a></p>
  <p><strong>Export Module:</strong><a href="https://github.com/NeuroML/pyNeuroML/blob/development/pyneuroml/swc/ExportNML.py">The export module can be accessed here</a> </p>
  <p><strong>Importance:</strong> This PR is critical for the project as it implements the core export functionality, enabling the conversion of SWC files to NeuroML format.</p>
</div>

<p>These Pull Requests represent significant steps in the development of the SWC to NeuroML converter. They showcase the iterative process of building, testing, and refining the tool throughout the Google Summer of Code period. The pending PR for the NeuroML Export Module is particularly crucial as it completes the primary functionality of the converter.</p>