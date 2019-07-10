# Guide-to-Access-Jupyter-Notebook-Running-on-VMware

It is a concise guide about how to access a jupyter notebook running in a local Linux virtual machine of VMware.

Host machine OS: Win10
Virtual machine OS: Ubuntu 16.04
The steps below may not all be necessary, while I am to lazy to check which are necessary ones.
Assume you have already installed jupyte notebook and can access it in your virtual machine.

Step 1: Turn off firewall of virtual machine. Commands: (need root privilege)

```
ufw disable
iptables -P INPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -P OUTPUT ACCEPT 
iptables -F 
```

Reference: https://blog.csdn.net/fengpenglang/article/details/6775114

Step 2: Modify Jupyter configuration in virtual machine.

```
jupyter notebook --generate-config
```

Then a file will be generated and its path will be shown.

Get IP address of your virtual machine:

```
ifconfig
```

Then you can see:

```
inet addr:[IP address of your virtual machine]
```

Edit the file generated:

```
c.NotebookApp.ip = '[IP address of your virtual machine]'
c.NotebookApp.open_browser = False
```

Step3:
Now you can start your Jupyter in virtual machine:

```
jupyter notebook
```

Cpoy the url generated to a browser in your host machine and you can see the familiar interface of Jupyter.




