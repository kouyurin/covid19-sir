CovsirPhy: COVID-19 analysis with SIRs
======================================

|PyPI version| |Downloads| |PyPI - Python Version| |Build Status|

|GitHub license| |Maintainability| |BCH compliance|

`Documentation <https://lisphilar.github.io/covid19-sir/index.html>`__
\| `Installation/Dataset
preparation <https://lisphilar.github.io/covid19-sir/INSTALLATION.html>`__
\| `Quickest
usage <https://lisphilar.github.io/covid19-sir/usage_quickest.html>`__
\| `API
reference <https://lisphilar.github.io/covid19-sir/covsirphy.html>`__

CovsirPhy is a Python package for COVID-19 (Coronavirus disease 2019)
data analysis with SIR-derived ODE models. We can download datasets and
analyse it easily. This will be a helpful tool for data-informed
decision making. Please refer to "Method" part of `Kaggle Notebook:
COVID-19 data with SIR
model <https://www.kaggle.com/lisphilar/covid-19-data-with-sir-model>`__
to understand the methods.

Functionalities
---------------

-  Data preparation and data visualization
-  `Phase setting with S-R Trend
   analysis <https://lisphilar.github.io/covid19-sir/usage_phases.html>`__
-  Numerical simulation of ODE models

   -  Stable: SIR, SIR-D and SIR-F model
   -  Development: SIR-FV and SEWIR-F model

-  Phase-dependent parameter estimation of ODE models
-  Scenario analysis: Simulate the number of cases with user-defined
   parameter values

Inspiration
-----------

-  Monitor the spread of COVID-19
-  Keep track parameter values/reproductive number in each
   country/province
-  Find the relationship of reproductive number and measures taken in
   each country/province

If you have ideas or need new functionalities, please join this project.
Any suggestions with `Github
Issues <https://github.com/lisphilar/covid19-sir/issues/new/choose>`__
are always welcomed. Please read `Guideline of
contribution <https://lisphilar.github.io/covid19-sir/CONTRIBUTING.html>`__
in advance.

Installation and dataset preparation
------------------------------------

We have the following options to start analysis with CovsirPhy. Datasets
are not included in this package, but we can prepare them with
``DataLoader`` class.

+--------------------------------+----------------+---------------------------------------+
|                                | Installation   | Dataset preparation                   |
+================================+================+=======================================+
| Standard users                 | pip/pipenv     | Automated with ``DataLoader`` class   |
+--------------------------------+----------------+---------------------------------------+
| Developers                     | git-cloning    | Automated with ``DataLoader`` class   |
+--------------------------------+----------------+---------------------------------------+
| Kagglers (local environment)   | git-cloning    | Kaggle API and Python script          |
+--------------------------------+----------------+---------------------------------------+
| Kagglers (Kaggle platform)     | pip            | Kaggle Datasets                       |
+--------------------------------+----------------+---------------------------------------+

\ `Installation and dataset
preparation <https://lisphilar.github.io/covid19-sir/INSTALLATION.html>`__
explains how to install and prepare datasets for all users.

Stable versions of Covsirphy are available at `PyPI (The Python Package
Index): covsirphy <https://pypi.org/project/covsirphy/>`__ and supports
Python 3.7 or newer versions.

::

    pip install covsirphy --upgrade

Development versions are in `GitHub repository:
CovsirPhy <https://github.com/lisphilar/covid19-sir>`__.

::

    !pip install "git+https://github.com/lisphilar/covid19-sir.git#egg=covsirphy"

| Main datasets will be retrieved via `COVID-19 Data
  Hub <https://covid19datahub.io/>`__ and the citation is
| Guidotti, E., Ardia, D., (2020), "COVID-19 Data Hub", Working paper,
  doi: 10.13140/RG.2.2.11649.81763.

Usage
-----

Please read the following documents.

-  `Usage (quickest
   version) <https://lisphilar.github.io/covid19-sir/usage_quickest.html>`__
-  `Usage (quick
   version) <https://lisphilar.github.io/covid19-sir/usage_quick.html>`__
-  `Usage (details:
   phases) <https://lisphilar.github.io/covid19-sir/usage_phases.html>`__
-  Example codes in `"example" directory of this
   repository <https://github.com/lisphilar/covid19-sir/tree/master/example>`__
-  `Kaggle: COVID-19 data with SIR
   model <https://www.kaggle.com/lisphilar/covid-19-data-with-sir-model>`__

License: Apache License 2.0
---------------------------

Please refer to
`LICENSE <https://github.com/lisphilar/covid19-sir/blob/master/LICENSE>`__
file.

Citation
--------

CovsirPhy Development Team (2020), CovsirPhy, Python package for
COVID-19 analysis with SIR-derived ODE models,
https://github.com/lisphilar/covid19-sir

Related work
------------

| Method of analysis in CovsirPhy:
| Lisphilar (2020), Kaggle notebook, COVID-19 data with SIR model,
  https://www.kaggle.com/lisphilar/covid-19-data-with-sir-model

| Reproduction number evolution in each country:
| Ilyass Tabiai and Houda Kaddioui (2020), GitHub pages, COVID19 R0
  tracker, https://ilylabs.github.io/projects/COVID-trackers/

.. |PyPI version| image:: https://badge.fury.io/py/covsirphy.svg
   :target: https://badge.fury.io/py/covsirphy
.. |Downloads| image:: https://pepy.tech/badge/covsirphy
   :target: https://pepy.tech/project/covsirphy
.. |PyPI - Python Version| image:: https://img.shields.io/pypi/pyversions/covsirphy
   :target: https://badge.fury.io/py/covsirphy
.. |Build Status| image:: https://semaphoreci.com/api/v1/lisphilar/covid19-sir/branches/master/badge.svg
   :target: https://semaphoreci.com/lisphilar/covid19-sir
.. |GitHub license| image:: https://img.shields.io/github/license/lisphilar/covid19-sir
   :target: https://github.com/lisphilar/covid19-sir/blob/master/LICENSE
.. |Maintainability| image:: https://api.codeclimate.com/v1/badges/eb97eaf9804f436062b9/maintainability
   :target: https://codeclimate.com/github/lisphilar/covid19-sir/maintainability
.. |BCH compliance| image:: https://bettercodehub.com/edge/badge/lisphilar/covid19-sir?branch=master
   :target: https://bettercodehub.com/