# Run TensorFlow on EC2 GPUs

## Find a working AMI
There's quite a bit that has to happen to get Tensorflow working on a GPU. It will take you [several hours to get working from scratch](http://eatcodeplay.com/installing-gpu-enabled-tensorflow-with-python-3-4-in-ec2/).

You can skip this by using a working AMI. 

I have an AMI that I built off of [@erikbern's TensorFlow GPU AMI](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Images:visibility=public-images;search=ami-cf5028a5;sort=name) ([provisioning script](https://gist.github.com/erikbern/78ba519b97b440e10640))


To get it, go to [your ec2 dashboard](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Images:visibility=public-images;search=ami-933d39f9;sort=name) and search public repos for `ami-933d39f9`

## Configure your instance

Choose a `g2.2xlarge` instance with 32 GB of storage. 

#### Security Groups

Make sure you open up port 22 for ssh and ports 443 and 8888 for accessing Jupyter notebooks. You can choose to allow from any IPs (shown below) or limit to custom addresses if you’d prefer.

| Type |    Protocol |    Port Range | Source
| SSH | TCP | 22 |   0.0.0.0/0
| HTTPS |   TCP | 443 |  0.0.0.0/0
| Custom | TCP | Rule |  TCP 8888    0.0.0.0/0


## Log into your box
As soon as your box finishes booting, it will serve Jupyter and should be accessible at:

```
https://your-ec2-instance.compute-1.amazonaws.com:8888
```

Enjoy!

## Optional - SSH into your box

You'll likely want to SSH into your box at some point in order to pull a new version of tensorflow or to update your Jupyter config in `~/.jupyter/jupyter_notebook_config.py`. Follow these instructions to SSH in.

#### Create a keypair
https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs:sort=keyName

I named mine `nottombrown-useast`

Download it and save it in `~/.ssh/`

Change the security settings

``` bash
# local
cert=~/.ssh/nottombrown-useast.pem
chmod 400 $cert
```

#### SSH into your box

Find the public URL of your new box

https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceId

Mine was `ec2-54-128-206-117.compute-1.amazonaws.com`

SSH in:
``` bash
# local 
ip=ec2-54-128-206-117.compute-1.amazonaws.com
user=ubuntu
ssh -i $cert $user@$ip
```

## Optional - Add a password to Jupyter

This machine is disposable and not connected to anything else valuable, so it should be okay to leave it without auth. However if you'd ike to have things protected, you can follow these instructions to [add a password to jupyter](python/add-a-password-to-jupyter.md).

