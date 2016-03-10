## Install Jupyter on Ubuntu

``` bash

sudo apt-get install build-essential python-dev python-setuptools \
                     python-numpy python-scipy \
                     libatlas-dev libatlas3gf-base \
                     python-matplotlib


sudo pip install jupyter
jupyter notebook --certfile=~/certs/mycert.pem --keyfile ~/certs/mycert.key
```
