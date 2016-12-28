# opticalmaterialspy
Python library with optical material properties.

This library provides a common interface to access the optical properties of
materials.  The main optical properties include:

* permittivity (and derivatives with respect to wavelength),
* refractive index (and derivatives with respect to wavelength),
* group velocity and group velocity refractive index,
* group velocity refractive index, and
* group velocity dispersion.

All properties are calculate from the Sellmeier equation of the material.  In
order to access all the above properties, minimally, the Sellmeier equation
of the desired material should be added (if it isn't already).  Many materials
already exist as an example.

## Installation
There are three main ways to install `opticalmaterialspy`.

* pip: `pip install opticalmaterialspy`
* setuptools: `cd opticalmaterialspy && python setup.py install`
* Arch Linux: `yaourt -S python-opticalmaterialspy`

### Dependencies
If installing using the [Arch Linux AUR package](https://aur.archlinux.org/packages/python-opticalmaterialspy/), dependencies will be automatically downloaded and installed, if not, one should ensure the following
dependencies are installed:

* [setuptools](https://pypi.python.org/pypi/setuptools),
* [numpy](http://www.numpy.org/), and
* [scipy](https://www.scipy.org/).

## Features
The main reasons to consider this library include:

* generic and simple interface for all materials,
* adding a new material only requires implementing one function,
* there is already a class written to generically accept a material from a text file, and
* intelligently works out what units the wavelengths being used are (see example).

## Examples
### Example 1: Optical parameters for SiO2
#### Python Script

	import opticalmaterialspy as mat

	m = mat.SiO2()

	# Refractive index @ 1550nm.
	print('n(1.55e-6m):', m.n(1.55e-6)) # Knows 1.55e-6 must be [m].
	print('n(1.55um):', m.n(1.55)) # Knows 1.55 must be [um].
	print('n(1550nm):', m.n(1550)) # Knows 1550 must be [nm].

	# Group velocity refractive index @ 900nm.
	print('n_gv(900nm):', m.ng(900))

	# Group velocity dispersion @ 808nm.
	print('GVD(0.808um):', m.gvd(0.808))
	
#### Output
	n(1.55e-6m): 1.4440236217
	n(1.55um): 1.4440236217
	n(1550nm): 1.4440236217
	n_gv(900nm): 1.46462460402
	GVD(0.808um): 3.59254440673e-26 

## Contributions
If you add functionality, especially new materials, I'd appreciate you send me a pull request,
or email the code to me so we can all benefit.