# Use docker for versioning your work

You can use docker for quickly versioning your work building an image. This is useful for places where you can't mount easily but don't want to lose progress

Let's say you're running the image `tensor` in a container called `tensor_container`

    docker run -p 8888:8888 -it --memory=8g --name=tensor_container tensor


Commit your changes to a new tagged image, `--pause=false` lets you keep your connection to it open, but causes a risk of corruption.

    docker commit --pause=false tensor_container tensor:pickled

On OSX, the images that you create will be stored in the directory of you VirtualBox application
