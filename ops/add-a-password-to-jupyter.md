## Add a password to Jupyter

First, generate the initial config and generate the password you’ll use to log in to Jupyter in the browser.


``` bash
# ec2
jupyter notebook --generate-config

key=$(python -c "from notebook.auth import passwd; print(passwd())")

# When prompted you'll need to specify a password
```

Next, we’ll create the certificate.

``` bash
cd ~
mkdir .certs
cd .certs
certdir=$(pwd)
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.key -out mycert.pem
# You'll be prompted to enter values for the cert,
# but it doesn't much matter, you can just leave them all blank.
```

And finally setup the Jupyter config with our cert, password and port.

``` bash
cd ~
sed -i "1 a\
c = get_config()\\
c.NotebookApp.certfile = u'$certdir/mycert.pem'\\
c.NotebookApp.ip = '*'\\
c.NotebookApp.open_browser = False\\
c.NotebookApp.password = u'$key'\\
c.NotebookApp.port = 8888" .jupyter/jupyter_notebook_config.py
```
