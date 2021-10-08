mtl
===

.. image:: https://badge.fury.io/py/mtl.svg
    :target: https://badge.fury.io/py/mtl

``mtl`` (**m**\ oving **t**\ ime-**l**\ apse) is a ``python`` tool to create time lapse animation from photos taken not from a fixed camera (hence 'moving') with identifiable markers.

``mtl`` align time series photos with markers (3 or 4 markers) provided as .TPS file (digitized with `TPSDig software <http://life.bio.sunysb.edu/morph/soft-dataacq.html>`_), and output the aligned photos and time-lapse movie.

.. image:: images/demo.gif

*Left: unaligned photo sequence; Right: aligned by* ``mtl``

requires
--------
``mtl`` is based on `OpenCV <https://opencv.org/>`_'s [#]_ implementation of affine transformation (with 3 markers provided) and perspective transformation (with 4 markers provided) [#]_.

Output of time-lapse video is based on `ffmpeg <https://www.ffmpeg.org/>`_ [#]_. To use ``mtl``, both ``OpenCV`` and ``ffmpeg`` are required.

how to use?
-----------
1. Use as a ``python`` package. ``mtl`` is on `PyPI <https://pypi.python.org/pypi/mtl>`_ and can be installed with ``pip`` (in command line, i.e. ``cmd`` in Windows [#]_ / ``terminal`` in Unix systems):

.. code:: bash

   pip install mtl

2. Directly use the ``mtl.py`` ``python`` module, if you prefer. Download the `file <https://github.com/jinyung/mtl/blob/master/mtl/mtl.py>`_.

``mtl`` can be directly used as command line script, with the following arguments:

  -h, --help         show this help message and exit
  -t, --tps 	     path to tps file containing landmarks for alignments
  -i, --img	     path to the directory containing images to be aligned
  -s, --sep          separator between individual and time in image name.
                     NOTE: use single quote (') for special character in Unix
                     systems

Alternatively, ``mtl`` can be imported into ``python`` (in ``python``):

.. code:: python

  from mtl import align

The main function of ``mtl`` is ``align``, which provides more options. For further details run (in ``python``):

.. code:: python

  help(align)

preparing images and markers file
---------------------------------
``mtl`` supports batch processing of multiple time series photos. Different time series (such as 'individuals') and time points should be indicated in the file name of the images. For examples, ``1-1.tif``, ``1-2.tif``, ..., ``1-100.tif`` and ``a-1.tif``, ``a-2.tif``, ..., ``a-100.tif`` will be processed as two different time series of '1' and 'a' with time points of 1, 2, ..., 100. These images should be placed in a single directory. A dash '-' is used to separate the time series and time points here so this should be instructed to the program. Only a single ``.TPS`` file is required for processing multiple time series photos, and it should contains markers for all images in the directory to be processed.

application
-----------
This tool was written for a friend's thesis, for monitoring organism's motility:

  Lin, J-C. (2018). Effects of water-flow and distance from neighbours on the mobility of the turtle barnacle *Chelonibia testudinaria* (Crustacea: Cirripedia). (MSc Dissertation). National Taiwan Ocean University. Available at: https://hdl.handle.net/11296/8ue54q

Which resulted in this publication:

  `Five hundred million years to mobility: directed locomotion and its ecological function in a turtle barnacle <https://doi.org/10.1098/rspb.2021.1620>`_


notes
-----
.. [#] `OpenCV's installation guide for Windows <http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_setup/py_setup_in_windows/py_setup_in_windows.html>`_; `Installation guide for Debian systems <https://milq.github.io/install-opencv-ubuntu-debian/>`_.

.. [#] A nice explanation on the transformation methods can be found `here <https://docs.opencv.org/3.2.0/da/d6e/tutorial_py_geometric_transformations.html>`_.

.. [#] `FFmpeg's installation guide for Windows <https://www.wikihow.com/Install-FFmpeg-on-Windows>`_; In Ubuntu it can be installed with ``apt`` (``apt-get install ffmpeg``)

.. [#] `Use pip in Windows <https://projects.raspberrypi.org/en/projects/using-pip-on-windows>`_
