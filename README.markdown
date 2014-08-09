# Docker Minecraft Overviewer

Base image for rendering a Minecraft world with [Minecraft Overviewer](http://overviewer.org/).

## Building 

Create the image `nightfly/minecraft-overviewer` by running this is the docker-minecraft-overviewer directory:

```sh
docker build --tag=nightfly/minecraft-overviewer
```

## Volumes

### Config file
By default the config file from `assets/app/config.py` is run at `/app/config.py`. 
If you wanna customize the render options you should mount your own config file over `/app/config.py`

### Default world and render directory (required)
By default the world is rendered from `/app/world` to `/app/render`.

### Texturepath (required)
The texturepath is where Minecraft Overviewer sources textures to render the map with. 
By default the texture path is set to `/app/textures.zip` but there is nothing at this location.
You must either supply a texture pack or minecraft client jar file in a derived image or mount one at this location.

## Example Usage

```sh
$ docker run --rm -v $HOME/.minecraft/saves/world:/app/world -v $HOME/render:/app/render -v $HOME/versions/1.7.10/1.7.10.jar:/app/textures.zip -u 1000 nightfly/minecraft-overviewer
```
