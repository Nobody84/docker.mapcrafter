# Mapcrafter - A Minecrafter world renderer

![Server Logo](https://git.drueke.biz/cdrueke/images/raw/master/logos/mapcrafter.png)
## Summary
>Mapcrafter is a high performance Minecraft map renderer written in C++. It renders Minecraft worlds to a bunch of images which are viewable in any webbrowser using Leaflet.js.
>Mapcrafter is free software and available under the GPL license. You can access the latest source code of Mapcrafter on GitHub: http://github.com/mapcrafter/mapcrafter

[Moritz Hilscher: https://github.com/mapcrafter/mapcrafter]

## Volumes
* render configuration
```
-v /mnt/user/data/mapcrafter/render.conf:/render.conf
```
* minecraft world files.
```
-v /mnt/user/data/mapcrafter/worlds:/worlds/
```
* rendered maps
```
-v /mnt/user/data/mapcrafter/www/:/www/
```

## Remarks
You can freely choose the location of the input (minecraft worlds) or the output (rendered maps) direcotry within the docker container. You only have to take account to it wihtin your render.conf.
There is only one restriction. The renderer is able to work with multiple input directories, but has only one output directory.
```
# output path of the renderer
output_dir = /www

# define yout world file locations here
[world:server1]
input_dir = /worlds/server1/world

[world:server2]
input_dir = /worlds/server2/world
```

## Start rendering
```
docker run -d --name=mapcrafter -v /mnt/user/data/mapcrafter/render.conf:/render.conf:rw -v /mnt/user/data/mapcrafter/worlds/:/worlds/:rw -v /mnt/user/data/mapcrafter/www/:/www/:rw topdockercat/mapcrafter
```