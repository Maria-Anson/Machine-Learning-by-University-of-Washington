# Where should my files go?
> 
> * * *
> 
> In demos and programming assignments, you will be asked to download notebooks and datasets. **This guide will show you where to place those files, so that IPython notebook can find them.**
> 
> ## Option 1: Place your folders and files where Jupyter can find them by default
> 
> 1.  Launch the Jupyter Notebook by typing
> 
> <pre contenteditable="false" data-language="plain_text" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> jupyter notebook
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> in the command line (Mac & Linux) or Command Prompt (Windows). You should be greeted in the web browser with the main page:
> 
> ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/c1Rys-c0EeiaxBKyA9PBAg_0fd42cea951cfa965eac6e2bfd65cf82_where_to_save_files_welcome.png?expiry=1593648000000&hmac=JnYP7Z84QD_pm2KaJ3PgQdNz_rvsJot2L1TuxZGhncM)
> 
> 2\. From the top right, find the button labeled "New▾". Click the button to get a drop-down menu, and select "Python 3" under the sub-heading "Notebook" This should create a new notebook inside the home directory of Jupyter notebook.
> 
> ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/nXo_B-c0EeiAgQrXx6bp4g_c62e9264e21354f29695b8560675f114_where_to_save_files_select_python3.png?expiry=1593648000000&hmac=5NjqL1qhZ6-f28eHoq4SgYG0OP9rC9uvNKR44IDY3t8)
> 
> 3\. In the new notebook, run
> 
> <pre contenteditable="false" data-language="python" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> import os
> 
> print os.getcwd()
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> to obtain the full path of the **home directory of Jupyter notebook**. **This path is where your files should go.** Highlight the path and copy it.
> 
> 4\. Place any files (notebooks and datasets) under this home directory using your file browser. You may organize your files using sub-folders.
> 
> ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/HeWmlec2EeilxxL_ZeRz_A_df664bc96abddf40e48c2f2070a6d96f_where_to_save_files_finder.png?expiry=1593648000000&hmac=F2m210lmJ0aP9YMwf8ONVZ7mt06_vZ-EaWAFGJlk89s)
> 
> 5\. All files and folders placed inside the home folder will appear in the main page:
> 
> ![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/NWwkcec2EeilxxL_ZeRz_A_d7e3362b0158884b8d5d04a8e0080d83_where_to_save_files_final.png?expiry=1593648000000&hmac=ci8vjdjLoRzIzG9NTZq-EaZoqopC8xuPz-klwXj_W4I)
> 
> ## Option 2: run Jupyter Notebook from where the files are
> 
> If you feel comfortable moving around the file system via command line, you may also choose to store your files wherever you like, then simply navigate to that directory and run the notebook there. For example, on command line in Mac/Linux, this looks like:
> 
> <pre contenteditable="false" data-language="plain_text" style="opacity: 1;" tabindex="0">
> 
> 1
> 
> 2
> 
> cd <directory_where_my_files_are_stored>
> 
> jupyter notebook
> 
> XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
> 
> </pre>
> 
> This option has the advantage of reducing clutter in your home directory.
>
> -- https://www.coursera.org/learn/ml-foundations/supplement/kRD6B/where-should-my-files-go#main
