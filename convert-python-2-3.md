# Convert Python scripts (and Jupyter Notebooks) from version 2 to 3
- Make sure `PATH` variable contains path to `<PYTHON INSTALLATION>/Tools/scripts`
- Make sure Python3 is installed

## .py
- Go to folder where `some_python2_file.py` file is located using a command prompt
- Run `2to3 some_python2_file.py -w`
- This overwrites Python2 code with Python3 code and creates a Python2 backup file

## .ipynb
- Run `pip install jupyter_contrib_nbextensions` using a command prompt
- Run `jupyter contrib nbextension install --user` using a command prompt
- Go to folder where Python2 `some_python2_notebook.ipynb` is located using a command prompt
- Run `jupyter notebook` using a command prompt
- Click on **Nbextensions**
- Uncheck **Disable configuration for nbextensions without explicit compatibility**
- Look for **2to3 Converter**
- Mark the checkbox
- Open Python2 `some_python2_notebook.ipynb`
- Select all cells
- Click on airplane icon to convert selected cells to Python3
- Save notebook
