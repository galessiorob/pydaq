---
title: 'PYDAQ: Data Acquisition and Experimental Analysis with Python'
tags:
  - Python
  - Data Acquisition
  - Arduino
  - NIDAQ
  - System Identification
  - Mathematical Modeling
authors:
  - name: Samir Angelo Milani Martins
    orcid: 0000-0003-1702-8504
    corresponding: true
    affiliation: "1, 2"
affiliations:
  - name: Department of Electrical Engineering at Federal University of São João del-Rei, Brazil.
    index: 1
  - name: GCoM - Modeling and Control Group at Federal University of São João del-Rei, Brazil.
    index: 2
date: 09 March 2023
bibliography: paper.bib
---

# Summary

System identification, a pivotal research topic, seeks mathematical models derived from acquired data. One key contribution is the work of [@Lju1987], which has been extensively developed over the years [@MA2016], [@WMNL2019]. Among system identification tools, SysIdentPy [@Lacerda2020] employs Python for system modeling through empirical data, while [@ayala2020r] proposes model acquisition using the R language.

As highlighted by [@Lju1987], experimental data is essential for black-box models, making PYDAQ particularly valuable. PYDAQ, a Python tool, was primarily designed for experiments with empirical data, enabling data sending and acquisition via simple graphical user interfaces or the command line. With minimal code, and compatibility with market solutions like NIDAQ and Arduino, even researchers without programming experience can utilize PYDAQ for efficient data collection.

Subsequent sections will discuss PYDAQ's usability, its benefits, and its features that facilitate rapid and effective data acquisition, irrespective of a user's programming proficiency.

# Statement of Need

PYDAQ targets scientists or students aiming for simple and swift data acquisition with as few as three lines of code. It provides a solution for experimental data acquisition to signal generation, facilitated by a graphical user interface.

Moreover, advanced users can access PYDAQ through the command line, as detailed in the [documentation](https://samirmartins.github.io/pydaq/), integrating it seamlessly with renowned modeling tools.

The significance of PYDAQ is underscored by numerous papers, such as [@Yang2019] and [@Koerner2020], dedicated solely to data acquisition. This initial step in empirical scientific processes, as illustrated in [@Ostrovskii2020], shouldn't consume excessive researcher effort.

Furthermore, PYDAQ supports a variety of data acquisition cards, ranging from affordable Arduino boards to advanced NIDAQ devices. This compatibility ensures the feasibility of diverse experiments. With its command line accessibility, PYDAQ can also integrate with prominent mathematical tools like SysIdentPy [@Lacerda2020] or SciKitLearn [@scikit-learn].

While some packages, like [@Koerner2020], interact with NIDAQ devices, they often require extensive coding for basic data collection and are limited to pricier, proprietary boards. To the best of my knowledge, no open-source software offers a user-friendly graphical interface for immediate data collection with Python, a unique feature of PYDAQ.

Considering these attributes, PYDAQ serves as an ideal introduction to the System Identification research domain. It can also be employed in educational settings, including engineering courses and cost-effective laboratory setups, given the affordability and availability of Arduino boards. Graphical interfaces foster direct user engagement with the subject, a sentiment echoed by [@Silva_2018].

The upcoming sections will provide examples of using PYDAQ and outline potential areas for future research. Comprehensive details are available in the [documentation](https://samirmartins.github.io/pydaq/).

# Examples

To quickly install PYDAQ, use pip:

```console
pip install pydaq
```

\autoref{fig:nidaq_get_gui} and \autoref{fig:arduino_get_gui} depict 
the Graphical User Interface developed for Data Acquisition using Arduino or any NIDAQ board.

![Data Acquisition through NIDAQ.\label{fig:nidaq_get_gui}](../docs/img/get_data_nidaq.png){ width=20%, height=20%}

![Data Acquisition through Arduino.\label{fig:arduino_get_gui}](../docs/img/get_data_arduino.png){ width=20%, height=20%}

To start them, only three lines of codes (LOC) are necessary, including one for importing PYDAQ: 

```python
from pydaq.get_data import Get_data
# Class Get_data
g = Get_data()

# Arduino or NIDAQ - Use ONE of the following lines 
g.get_data_nidaq_gui() # For NIDAQ devices 
g.get_data_arduino_gui() # For arduino boards
```

Similarly, to send data, only three LOCs are required, as shown below:

```python
from pydaq.send_data import Send_data

# Class Send_data
s = Send_data()

# Arduino or NIDAQ - Use ONE of the following lines 
s.send_data_nidaq_gui()
s.send_data_arduino_gui()
```

If the user decides to save data, it will be stored in `.dat` format, using the 
path defined in the GUI (Desktop is the default path). \autoref{fig:data} shows an example of how data will be saved: i) one file (time.dat) 
with the timestamp, in seconds, when each sample was acquired; ii) file data.dat containing acquired values.

![Example of acquired data.\label{fig:data}](../docs/img/data.png){ width=20%, height=20%}

![GUI for sending data - Arduino.\label{fig:arduino_send_gui}](../docs/img/send_data_nidaq_gui.png){ width=20%, height=20%}

![GUI for sending data - NIDAQ.\label{fig:nidaq_send_gui}](../docs/img/send_data_arduino_gui.png){ width=15%, height=15%}

Once this code is executed, a Graphical User Interface (GUI) will appear on the screen, corresponding to the board chosen by the user, as illustrated in \autoref{fig:arduino_send_gui} and \autoref{fig:nidaq_send_gui}.

The options are intuitive and easy to navigate. For a more detailed explanation and for instructions on using these functionalities via the command line, readers are directed to the [documentation](https://samirmartins.github.io/pydaq/).

It's important to note that any signal can be generated and applied to a physical system using the provided GUI, with the chosen board being the primary limitation. Data can be generated manually or with a library (e.g., numpy) to produce signals such as sine waves, PRBS (Pseudo-Random Binary Signal), or any other signal that serves as a persistently exciting input, which is essential for system identification [@Lju1987], [@Bil2013].

A step-response is a standard method for testing a system and collecting data to derive a model, as well as to determine the system's time constant and gain. To streamline this process, a step-response GUI has been developed, visible in \autoref{fig:step_nidaq} and \autoref{fig:step_arduino}. To access it, users should enter the following command:

```python
from pydaq.step_response import Step_response

# Class Step_Response
s = Step_response()

# Arduino or NIDAQ - Use ONE of the following lines 
s.step_response_nidaq_gui()
s.step_response_arduino_gui()
```


![Step Response GUI - NIDAQ.\label{fig:step_nidaq}](../docs/img/step_response_nidaq_gui.png){ width=30%, height=30%}

![Step Response GUI - Arduino.\label{fig:step_arduino}](../docs/img/step_response_arduino_gui.png){ width=20%, height=20%}

Here the user can define when the step will be applied, as well as where data will be saved.
\autoref{fig:data_sent} and \autoref{fig:step_data} show data that were empirically-acquired 
with PYDAQ. In the figures the user will find labels, functionality (Sending Data/Data Acquisition/Step Response), 
device/channel (for NIDAQ boards) or COM port used (for Arduino devices).


![Data acquired using a NIDAQ board.\label{fig:data_sent}](../docs/img/sending_data_nidaq.png){ width=40%, height=40%}

![Data generated by a step-response experiment.\label{fig:step_data}](../docs/img/step_response_arduino.png){ width=40%, height=40%}


The examples provided above highlight some of PYDAQ's features. For a deeper understanding and guidance on using the command line, please refer to the [complete documentation](https://samirmartins.github.io/pydaq/).

# Future Work
Upcoming versions of PYDAQ will incorporate:
- Real-time and data-driven system identification using both linear and nonlinear methodologies.
- Implementation of real-time model-based controllers.
- The capability to save data on an SQL server.


# References
