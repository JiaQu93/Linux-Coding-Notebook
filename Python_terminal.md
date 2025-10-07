# Running Python Scripts on a remote server
This guide shows how to run a long Python job on a remote server

## `screen` 
`screen` creates a virtual terminal on the server that keeps running in the background, independent of your network session.

### 1. Start a new screen session
Open your terminal or JupyterLab Terminal and run:  
`screen -S myjob`  
This creates and attaches to a new screen session named myjob.  

### 2. Activate your conda environment  
Inside screen:  
`conda activate rna_seq`  
Now the environment is active for your Python job.  

**Note** How to check current env/kernel:   
Jupyter Notebook cell   
`import sys`   
`sys.executable`

### 3. Run your Python script
`python download_abc.py`  
Your script is now running inside the screen session.

### 4. Detach (let it run in the background)
Press the following key combo:
`Ctrl + A, then D`  
This detaches the session but keeps it alive in the background. You’ll see something like:
[detached from 12345.myjob]  
Now you can safely log out, close SSH, or lose connection.

### 5. Check running sessions
`screen -ls`  
Example output:
There is a screen on:
    12345.myjob  (Detached)
1 Socket in /run/screen/S-username.

### 6. Reconnect to your session
`screen -r myjob`   
You’ll re‑enter the running terminal and can see your script’s output.   

### 7. End or delete a screen session  
When your script finishes, you can type:  
`exit` or press `Ctrl + D` to close the screen session.

To remove a session manually:
`screen -S myjob -X quit`


