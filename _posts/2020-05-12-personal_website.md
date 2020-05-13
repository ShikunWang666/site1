---
layout: post
title: How to use Jupyter notebook to analyze data using R on server?
---

In my research, I find it more convenient to use Jupyter notebook to analyze data using R on server. You can run code and visualize the results instantly, and no need to download the figures (similar to R markdown)! Here are the steps I followed to make this work. Just for your information. 😊

## Step 0: Login server
Login VPN if you are off the LAN of your server.
In terminal, type `ssh usrname@serveraddress`

## Step 1: Install Anaconda3 in your working directory (ask your admin)
## Step 2: Install R within Anaconda3
In terminal, type:
`conda create -n r_env r-essentials r-base`
`conda activate r_env`
If you want to deactivate the R environment, type:
`conda deactivate`
Reference: https://docs.anaconda.com/anaconda/user-guide/tasks/using-r-language/

## Step 3: Prepare R for Jupyter notebook
In your working directory type
1. conda update ipython
2. conda install -c r ipython r-irkernel
3. (In R) install.packages(c('rzmq','repr','IRkernel','IRdisplay'))
4. IRkernel::installspec()
Reference: https://discuss.analyticsvidhya.com/t/how-to-run-r-on-jupyter-ipython-notebooks/5512/4

## Step 4: Test!
Create a new notebook on server by typing: 
`jupyter notebook --no-browser --port=8888`
then open a new terminal window (shortcut: command+T), and open a mapping
`ssh -N -f -L localhost:8889:localhost:8888 usrname@serveraddress`
In your browser, open a new page:
`localhost:8889`

Now you can see the notebook on your local browser. Click on "New" on top right corner, you can open a new R notebook. After finished using, save everything, click on "Logout", and go back to terminal type "killall ssh" to stop the mapping. 

![_config.yml]({{ site.baseurl }}https://petspruce.com/wp-content/uploads/2020/03/How-to-Train-a-Bengal-Cat.jpeg)
