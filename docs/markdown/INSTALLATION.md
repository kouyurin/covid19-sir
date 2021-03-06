# Installation and dataset preparation

## Options of installation
We have the following options to start analysis with CovsirPhy. Datasets are not included in this package, but we can prepare them with `DataLoader` class.

||Installation|Dataset preparation|
|:---|:---|:---|
|Standard users|pip/pipenv|Automated with `DataLoader` class|
|Developers|git-cloning|Automated with `DataLoader` class|
|Kagglers (local environment)|git-cloning|Kaggle API and Python script and `DataLoader`|
|Kagglers (Kaggle platform)|pip|Kaggle Datasets and `DataLoader`|


## Datasets to load
We will use the following datasets. Standard users and developers will retrieve main datasets from [COVID-19 Data Hub](https://covid19datahub.io/) using `covid19dh` Python package internally. We can get the citation list of primary source `covsirphy.DataLoader` class (refer to "Standard users" subsection). This description is from [COVID-19 Data Hub: Dataset](https://covid19datahub.io/articles/data.html).

### [COVID-19 Data Hub](https://covid19datahub.io/)
Guidotti, E., Ardia, D., (2020), "COVID-19 Data Hub", Journal of Open Source Software 5(51):2376, doi: 10.21105/joss.02376.

- The number of cases (JHU style)
- Population in each country
- Government Response Tracker (OxCGRT)

### [Datasets for CovsirPhy](https://github.com/lisphilar/covid19-sir/tree/master/data)
Lisphilar (2020), GitHub repository, COVID-19 dataset in Japan.  
- The number of cases in Japan

### How to request new data loader
If you want to use a new dataset for your analysis, please kindly inform us via [GitHub Issues: Request new method of DataLoader class](https://github.com/lisphilar/covid19-sir/issues/new/?template=request-new-method-of-dataloader-class.md). Please read [Guideline of contribution](https://lisphilar.github.io/covid19-sir/CONTRIBUTING.html) in advance.

## 1. Standard users
Stable versions of Covsirphy are available at [PyPI (The Python Package Index): covsirphy](https://pypi.org/project/covsirphy/) and support Python 3.6 or newer versions.
```
pip install --upgrade covsirphy
```

Development versions are in [GitHub repository: CovsirPhy](https://github.com/lisphilar/covid19-sir).
```
pip install --upgrade "git+https://github.com/lisphilar/covid19-sir.git#egg=covsirphy"
```

Then, download the datasets and save the data in `input` directory.
```Python
import covsirphy as cs
data_loader = cs.DataLoader("input")
jhu_data = data_loader.jhu()
japan_data = data_loader.japan()
population_data = data_loader.population()
oxcgrt_data = data_loader.oxcgrt()
```
If `input` directory has the datasets, `DataLoader` will load the local files. If the datasets were updated in remote servers, `DataLoader` will update the local files automatically.

We can get descriptions of the datasets and raw/cleaned datasets easily. As an example, JHU dataset will be used here.
```Python
# Description (string)
jhu_data.citation
# Raw data (pandas.DataFrame)
jhu_data.raw
# Cleaned data (pandas.DataFrame)
jhu_data.cleaned()
```
We can get COVID-19 Data Hub citation list of primary sources as follows.
```Python
data_loader.covid19dh_citation
```


## 2. Developers
Developers will clone this repository with `git clone` command and install dependencies with pipenv.
```
git clone https://github.com/lisphilar/covid19-sir.git
cd covid19-sir
pip install wheel; pip install --upgrade pip; pip install pipenv
export PIPENV_VENV_IN_PROJECT=true
export PIPENV_TIMEOUT=7200
pipenv sync --dev
```

Shell will be started with `pipenv shell` and `python` command.

Developers can perform tests with `pipenv run pytest -v --durations=0 --failed-first --maxfail=1 --cov=covsirphy --cov-report=term-missing --profile-svg` and call graph will be saved as SVG file (prof/combined.svg).

- Windows users need to install [Graphviz for Windows](https://graphviz.org/_pages/Download/Download_windows.html) in advance.
- Debian/Ubuntu users need to install Graphviz with `sudo apt install graphviz` in advance.

If you can run `make` command,

|||
|:---|:---|
|`make install`|Install pipenv and the dependencies of CovsirPhy|
|`make test`|Run tests using Pytest|
|`make docs`|Update sphinx document|
|`make example`|Run example codes|
|`make clean`|Clean-up output files and pipenv environment|

We can prepare the dataset with the same codes as that was explained in "1. Standard users" subsection.

## 3. Kagglers (local environment)
As explained in "2. Developers" subsection, we need to git-clone this repository and install the dependencies when you want to uses this package with Kaggle API in your local environment.

Then, please move to account page of Kaggle and download "kaggle.json" by selecting "API > Create New API Token" button. Copy the json file to the top directory of the local repository or "~/.kaggle". Please refer to [How to Use Kaggle: Public API](https://www.kaggle.com/docs/api) and [stackoverflow: documentation for Kaggle API *within* python?](https://stackoverflow.com/questions/55934733/documentation-for-kaggle-api-within-python#:~:text=Here%20are%20the%20steps%20involved%20in%20using%20the%20Kaggle%20API%20from%20Python.&text=Go%20to%20your%20Kaggle%20account,json%20will%20be%20downloaded)

We can download datasets with `pipenv run ./input.py` command. Modification of environment variables is un-necessary. Files will be saved in `input` directory of your local repository.

Note:  
Except for OxCGRT dataset, the datasets downloaded with `input.py` scripts are different from that explained in the previous subsections as follows.

- The number of cases (JHU) and linelist: [Novel Corona Virus 2019 Dataset by SRK](https://www.kaggle.com/sudalairajkumar/novel-corona-virus-2019-dataset)
- The number of cases in Japan: [COVID-19 dataset in Japan by Lisphilar](https://www.kaggle.com/lisphilar/covid19-dataset-in-japan)
- Population in each country:  [covid19 global forecasting: locations population by Dmitry A. Grechka](https://www.kaggle.com/dgrechka/covid19-global-forecasting-locations-population)
- Government Response Tracker (OxCGRT):  [Thomas Hale, Sam Webster, Anna Petherick, Toby Phillips, and Beatriz Kira. (2020). Oxford COVID-19 Government Response Tracker. Blavatnik School of Government.](https://github.com/OxCGRT/covid-policy-tracker)

Usage of `DataLoader` class is as follows. Please specify `local_file` argument in the methods.
```Python
import covsirphy as cs
data_loader = cs.DataLoader("input")
jhu_data = data_loader.jhu()
japan_data = data_loader.japan(local_file="./kaggle/input/covid_jpn_total.csv")
population_data = data_loader.population()
oxcgrt_data = data_loader.oxcgrt(local_file="./kaggle/input/OxCGRT_latest.csv")
```

(Optional) We can replace a part of JHU data with country-specific datasets.
As an example, we will use the records in Japan here because values of JHU dataset sometimes differ from government-announced values as shown in [COVID-19: Government/JHU data in Japan](https://www.kaggle.com/lisphilar/covid-19-government-jhu-data-in-japan).

```Python
jhu_data.replace(japan_data)
ncov_df = jhu_data.cleaned()
```

## 4. Kagglers (Kaggle platform)
When you want to use this package in Kaggle notebook, please turn on Internet option in notebook setting and download the datasets explained in the previous subsection "3. Kagglers (Kaggle platform)".

Then, install this package with pip command.
```
!pip install covsirphy
```

Then, please load the datasets with the following codes, specifying the filenames.
```Python
import covsirphy as cs
# The number of cases (JHU style)
data_loader = cs.DataLoader()
jhu_data = data_loader.jhu()
# (Optional) The number of cases in Japan
japan_data = cs.CountryData("/kaggle/input/covid19-dataset-in-japan/covid_jpn_total.csv", country="Japan")
japan_data.set_variables(
    date="Date", confirmed="Positive", fatal="Fatal", recovered="Discharged", province=None
)
# Population in each country
population_data = data_loader.population()
```

Note:  
Currently, OxCGRT dataset is not supported.


(Optional) We can replace a part of JHU data with country-specific datasets.
As an example, we will use the records in Japan here because values of JHU dataset sometimes differ from government-announced values as shown in [COVID-19: Government/JHU data in Japan](https://www.kaggle.com/lisphilar/covid-19-government-jhu-data-in-japan).

```Python
jhu_data.replace(japan_data)
ncov_df = jhu_data.cleaned()
```
