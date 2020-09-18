# Sphinx website development


## Sphinx website setup

* Create a virtual env
* Install sphinx

```
brew install sphinx-doc
pip install sphinx
```

* Setup Sphinx

```
#if needed
mkdir docs
cd docs
```

```
sphinx-quickstart
```

Sample settings:

```

> Separate source and build directories (y/n) [n]: n
> Project name: Amazon SageMaker Debugger
> Author name(s): Aaron Markham, Miyoung Choi
> Project release []: 1.0.0
> Project language [en]: en
```

* Setup the RTD theme

```
pip install sphinx-rtd-theme
```

Edit conf.py to change the theme to be `sphinx-rtd-theme`


```
html_theme = 'sphinx_rtd_theme'
```

* Generate stub documentation files


For `smdebug` this would be:

```
sphinx-apidoc -o . ../smdebug
```

* Add modules page to index.rst under the toctree (make sure modules is tabbed in)

* Other key updates to conf.py

```
# up at the top in the import section
sys.path.insert(0, os.path.abspath('../smdebug'))
autodoc_mock_imports = ["mxnet", "tensorflow", "torch"]
```

```
# down in extensions
extensions = [
'sphinx.ext.autodoc'
]
```
## Build the website

### Prerequisites
Sphinx v3.0.3 - check the Sphinx site for your operating system install.

Your Python3 environment requires several packages:
```
pip install sphinx sagemaker==1.7.2 smdebug mxnet tensorflow torch
```

### Generate the site

Use the following:
```
make html
```

Run a clean operation every once in while to see all warnings and errors.
```
make clean
```
