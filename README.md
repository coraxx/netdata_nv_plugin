# README #

[NetData](https://github.com/firehol/netdata/) plugin that polls Nvidia GPU data.

![nv plugin screenshot](http://semper.space/netdata_nv/screenshot01.png "Netdata nv plugin")


### Requirements ###

* Nvidia driver installed (this plugin needs the NVML library)
* nvidia-ml-py Python package (Python NVML wrapper)
    - install via `pip install nvidia-ml-py`
    - or copy `pynvml.py` from the "nvidia-ml-py" package (https://pypi.python.org/pypi/nvidia-ml-py/7.352.0) to `/usr/libexec/netdata/python.d/python_modules/`


### Installation ###

With default NetData installation copy the nv.chart.py script to `/usr/libexec/netdata/python.d/` and the nv.conf config file to `/etc/netdata/python.d/`.

Edit the config file to set options for extracted information.

Then restart NetData to activate the plugin.

To disable the nv plugin, edit `/etc/netdata/python.d.conf` and add `nv: no`.


### Legacy Mode ###

STILL UNDER CONSTRUCTION AND NOT OPERATIONAL AT THE MOMENT

With older GPUs like my Nvidia GeForce 9600m gt, the core clock cannot be read by the NVML lib. Only temperature and memory usage is displayed.
Set `legacy: True` in the `nv.conf` file to poll GPU and memory load via the nvidia-settings application (also installed with the Nvidia driver).


### Displayed Date ###

Depending on the Graphics card, these informations are extracted:

- GPU and memory load
- Free and used memory
- ECC errors (only for cards equipped with ECC memory e.g. Quadro cards)
- Temperature
- Fan speed
- Clock frequency for GPU core, SM and memory

Readouts for units (S-class systems) are integrated but not tested yet. This adds:

- intake, exhaust and board temperature
- PSU current, voltage and power
- Fan rpm


### Known Bugs ###

While making this plugin fit for Python 3 I encountered an old Python 2 style `print` in nvidia-ml-py's `pynvml.py` file. Line 1671 `print c_count.value` must be `print(c_count.value)`!
You can do this fix on your own or use the fixed version from this repo.


### License ###

The MIT License (MIT)
Copyright (c) 2016 Jan Arnold

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

### Version ###

v0.3 - potential bugs fixed
     - fit for Python >=2.6 and >=3.2 (see known bugs section)

v0.2 - code cleanup (thanks to @paulfantom for the feedback)

v0.1 - initial release



### Who do I talk to? ###

* Repo owner or admin
* Other community or team contact
