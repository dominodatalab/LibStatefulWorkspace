# LibStatefulWorkspace

Follow these steps:
1. Create a file called `requirements-custom.txt` in the `/mnt/code` folder
2. You will be installing libraries in the folder `/mnt/code/python/libraries`
3. In the `.gitignore` file specify that it ignore the folder and the sub-folders of `/mnt/code/python`


## Create a new Environment to install the libraries

You will need to add the following pre-run script in the Environment definition

```bash
#!/bin/bash
set -e
TARGET_PATH=/mnt/code/python/libraries
pip install --upgrade --target $TARGET_PATH -r /mnt/code/requirements-custom.txt
echo "Packages installed to $TARGET_PATH and PYTHONPATH updated."
```

## In the `.gitignore` file exclude the library folder

Add the folloing line at the end of your `.gitignore` file and commit the code
```
python/*/*
```

## Making the workspace aware of the new path

You can either update the `PYTHONPATH` to include the new path `/mnt/code/python/libraries`

```
export PYTHONPATH=/mnt/code/python/libraries
```

or you can explicitly add the path via code

```
import sys
sys.path.append("/mnt/code/python/libraries")
```

## All Set

Your custom libraries will not survive custom restarts