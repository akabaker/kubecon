Build Tools
-----------

Bad things
    * apt-get update
    * ADD/COPY

These problems have been solved before (in linux).

### Tool usability continuum
easy to use, comprehensive
available, trusted
fast, reliable

### Investigation, using distro tools to build container images
debian, debos
buildroot
yocto project (distribution builder)
guix sd (functional distro build concepts)


### Experiemnt 1, base os for golan apps
DebOs
    * easy to use
    * SBoM is meh

Yocto
    * not easy
    * image sizes are small tho
    * lots of effort
    * nice SBoM

Can we leverage package manager to only install what is required in img
    * Just enough OS
Not much support for cloud native

Takeaways, this still sucks?
Look at your container images
    * Dive (layout of container img)
    * Container-diff
    * Tern
DebOS is pretty good?