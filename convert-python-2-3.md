# Convert scripts and notebooks from Python2 to Python3
- Make sure `PATH` variable contains path to `<PYTHON INSTALLATION>/Tools/scripts`
- Make sure Python3 is installed

## .py
- Go to folder where `some_python2_file.py` file is located using a command prompt
- Run `2to3 some_python2_file.py -w`
- This overwrites Python2 code with Python3 code and creates a Python2 backup file

## .ipynb
- Run `pip install jupyter_contrib_nbextensions`
- Run `jupyter contrib nbextension install --user`
- Go to folder that contains `some_python2_notebook.ipynb` using a command prompt
- Run `jupyter notebook`

![Image](/img/convert-python-2-3-1.png)

- Click on **Nbextensions**

![Image](/img/convert-python-2-3-2.png)

- Uncheck **disable configuration for nbextensions without explicit compatibility**

![Image](/img/convert-python-2-3-3.png)

- Look for **2to3 Converter** and check it

![Image](/img/convert-python-2-3-4.png)

- Open Python2 `some_python2_notebook.ipynb`
- Select all cells

![Image](/img/convert-python-2-3-5.png)

- Click on airplane icon to convert selected cells to Python3

![Image](/img/convert-python-2-3-6.png)

- Save notebook

![Image](/img/convert-python-2-3-7.png)
