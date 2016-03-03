# Use docker for versioning your work

You can use docker for versioning your work. It's not as nice as git, but it gets the job done.

Let's say you're running the image `tensor` in a container called `tensor_container`

    docker run -p 8888:8888 -it --memory=8g --name=tensor_container tensor


Commit your changes to a new tagged image, `--pause=false` lets you keep your connection to it open, but causes a risk of corruption.

    docker commit --pause=false tensor_container tensor:pickled

On OSX, the images that you create will be stored in the directory of you VirtualBox application
