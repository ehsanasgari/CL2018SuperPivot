## (Step 0) Loging to the calculus server

Login to the sever and follow the steps!
```
ssh user@calculus.cis.lmu.de
```


## (Step 1) Miniconda installation

The first step is to install the latest version of conda on your home directory.

```
cd ~
curl -O https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

Then run the installation and follow the steps:
```
bash ./Miniconda3-latest-Linux-x86_64.sh
```

Then you need to add the conda to your path. Please replace the path with the path you are provided in the installation:
```
export PATH="/mounts/YOUR_MINI_CONDA_PATH/bin:$PATH"
```

Then you need to add conda channels:

```
conda config --add channels conda-forge
```


## (Step 2) Installation of dependencies in the virtual environment

The next step would be installation of the dependencies:

```
conda create --name CL2018 --file installations/env_linux.txt
```


Then you need to activate the created virtual environment:

```
source activate CL2018
```


## (Step 3) Running Jupyter Notebook on the server and view it on your laptop


### Run a Jupyter notebook on the server

Go to your home directory or any where on the server that you want to run some codes:
```
cd ~
```

Create a screen so that even when you are disconnected once, you can again access to the
Jupyter:

```
screen -S jupnote
```

* You can use Ctrl+D to detach the screen when you within the screen.
* -S is for starting a screen, later on to access this screen using 'screen -x jupnote'.

Use the following command to run the note book on the server on a specific port. Choose a number between 6666 to 9999:

```
useratserver@server$ ipython notebook --no-browser --port=7777
```

After running the above mentioned command you will get a URL like this:

```
http://localhost:7777/?token=208ac324a8d4c53e91f74921edfe02227a3324b5c86b5b29
```

This means that on the server on the port 7777 you can access a notebook on the directory you provided in the beginning.
If the specified port is busy, you will get a different port. Copy the token provided in the link.

For instance here is the token is:
```
208ac324a8d4c53e91f74921edfe02227a3324b5c86b5b29
```

You can use Ctrl+D to detach the screen and later use 'screen -x jupnote
to see this screen.

### Access the notebook via your laptop

Open the terminal on you laptop and run the following command.
Please modify the port on your laptop (here 8888) and the port on the server (here 7777)
and you username on calculus.

```
ssh -N -f -L localhost:8888:localhost:7777 youruser@calculus.cis.lmu.de
```

Now you can simply open the following address on your browser and open the provided notebook.
Please make sure to modify the token, with token you got on the server:

```
localhost:8888/?token=208ac324a8d4c53e91f74921edfe02227a3324b5c86b5b29
```

'
