<p align="center">
  <img src="logo/pydaq-logo.png" alt= “PYDAQ” class=“center” width="50%" height="50%">
</p> 

[![PyPI version](https://img.shields.io/pypi/v/pydaq?color=a26969)](https://github.com/samirmartins/pydaq)
[![License](https://img.shields.io/pypi/l/pydaq?color=a26969)](https://opensource.org/licenses/BSD-3-Clause)
[![python](https://img.shields.io/pypi/pyversions/pydaq?color=a26969)](https://pypi.org/project/pydaq/)
[![status](https://img.shields.io/pypi/status/pydaq?color=a26969)](https://pypi.org/project/pydaq/)
[![contributors](https://img.shields.io/github/contributors/samirmartins/pydaq?color=a26969)](https://github.com/samirmartins/pydaq/graphs/contributors)
[![downloads](https://img.shields.io/pypi/dm/pydaq?color=%23A26969)](https://pypi.org/project/pydaq/)
[![openissues](https://img.shields.io/github/issues/samirmartins/pydaq?color=a26969)](https://github.com/samirmartins/pydaq/issues)
[![issuesclosed](https://img.shields.io/github/issues-closed-raw/samirmartins/pydaq?color=a26969)](https://github.com/samirmartins/pydaq/issues)
[![forks](https://img.shields.io/github/forks/samirmartins/pydaq?color=a26969&style=social)](https://github.com/samirmartins/pydaq/network/members)
[![stars](https://img.shields.io/github/stars/samirmartins/pydaq?color=a26969&style=social)](https://github.com/samirmartins/pydaq/stargazers)




# PYDAQ - Data Acquisition and Experimental Analysis with Python


----
Using Python for applications with experimental data (Arduino and NIDAQ boards)
----

This package was originally designed for using experimental devices for data acquisition and as a signal generator, particularly during experiments like step-response tests.

However, PYDAQ can be used to acquire and send signals from any system using various boards. You can explore more in the [jupyter notebook examples folder](examples). Users can interact with PYDAQ through a Graphical User Interface (GUI) or the command line, enabling the generation of customized signals that can be easily applied to a system.

It's important to highlight that this application simplifies data acquisition and empirical experiments, making them quicker and more intuitive. This becomes particularly crucial when users require empirical data to construct both linear and nonlinear black-box models, which are commonly used in research projects for forecasting and model-based control schemes.

The provided code allows users to save acquired data in .dat files to a specified path (or to the Desktop if no path is provided). Additionally, users can send their own data, which could be any nonlinear input signal. [It's strongly advised to check the documentation for more details](https://samirmartins.github.io/pydaq/).

Below, you will find:

- Installation and Requirements
- Quick View and Main Features
- Using the Graphical User Interfaces
- Screenshots

---
Installation and Requirements
---

The most straightforward method to install PYDAQ is via pip:

```console
pip install pydaq
```

For PYDAQ to function correctly, the following requirements must be met:

- The appropriate driver for the board in use (either Arduino or National Instruments NIDAQ).
- `nidaqmx` (>=0.6.5): For data acquisition from National Instruments Boards.
- `matplotlib` (>=3.5.3): For visualization.
- `numpy` (>=1.22.3): For data processing.
- `PySimpleGUI` (>=4.60.3): Provides the Graphical User Interface.
- `PyQt5`: Serves as the backend for PySimpleGUI.
- `pyserial` (>=3.5): For managing data transfer with Arduino.


---
Quick view and Main features
---

| Feature                      | Description                                                                                                                                                                                                                                         |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Send Data (NIDAQ)            | Allows users to send data via any NIDAQ board using a graphical user interface.                                                                                                                                                                      |
| Send Data (Arduino)          | Allows users to send data via any Arduino board using a graphical user interface.                                                                                                                                                                    |
| Get Data (NIDAQ)             | Users can retrieve data from a NIDAQ board, utilizing various terminal configurations (Diff, RSE, NRSE), and sample time, among others. The acquired data can be saved and plotted for additional applications.                                          |
| Get Data (Arduino)           | Users can retrieve data from an Arduino board, with several available options. Acquired data can be saved and plotted for subsequent applications.                                                                                                    |
| Step Response (NIDAQ)        | Enables users to conduct an automatic step response experiment using a NIDAQ board. The data generated by the experiment can be saved for further applications, such as deriving linear and nonlinear models.                                       |
| Step Response (Arduino)      | Enables users to conduct an automatic step response experiment using an Arduino board. The data generated by the experiment can be saved for subsequent applications, such as deriving linear and nonlinear models. |

---
Using GUIs (more details in [documentation](https://samirmartins.github.io/pydaq/) and [jupyter notebook examples](examples)):
---

#### Data acquisition (NIDAQ):

```python
from pydaq.get_data import Get_data
g = Get_data()
g.get_data_nidaq_gui()
```

#### Data acquisition (Arduino):

```python
from pydaq.get_data import Get_data
g = Get_data()
g.get_data_arduino_gui()
```

#### Sending data (NIDAQ):

```python
from pydaq.send_data import Send_data
s = Send_data()
s.send_data_nidaq_gui()
```

#### Sending data (Arduino):

```python
from pydaq.send_data import Send_data
s = Send_data()
s.send_data_arduino_gui()
```

#### Step response (NIDAQ):

```python
from pydaq.step_response import Step_response
s = Step_response()
s.step_response_nidaq_gui()
```

#### Step response (Arduino):

```python
from pydaq.step_response import Step_response
s = Step_response()
s.step_response_arduino_gui()
```

---
Screnshots
---

### Graphical User Interfaces - NIDAQ

![](docs/img/get_data_nidaq.png)

![](docs/img/send_data_nidaq_gui.png)

![](docs/img/step_response_nidaq_gui.png)

### Graphical User Interfaces - Arduino

![](docs/img/get_data_arduino.png)

![](docs/img/send_data_arduino_gui.png)

![](docs/img/step_response_arduino_gui.png)

### Acquired/Sending data and step response - NIDAQ and Arduino

![](docs/img/step_response_arduino.png)

![](docs/img/step_response_nidaq.png)


![](docs/img/sending_data_nidaq.png)

![](docs/img/sending_data_arduino.png)

![](docs/img/acquired_data_nidaq.png)

![](docs/img/acquired_data_arduino.png)

### Data in .dat format

![](docs/img/data.png)

---
Contributing
---

You are more than welcome to make your contribution and submit a pull request. To contribute, [read this guide](/CONTRIBUTING.md).
