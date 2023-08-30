This snap contains the Arc Aurora Cursors Theme. Arc Aurora Cursors is an x-cursor theme inspired by macOS and based on capitaine-cursors.  

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/arcaurora-cursors)  

---

## Attributions  

All credit goes to the original cursor developer @yeyushengfan258.  
Thanks to @jollygoose for the template building a snap of a cursor theme and his/her useful instructions which I copied here.  


## Building the snap locally

Requirements
* [snapcraft](https://snapcraft.io/snapcraft) (```snap install snapcraft```)
* [multipass](https://snapcraft.io/multipass) (```snap install multipass```)
* Copy ArcAurora-cursors.zip file into arcaurora-cursors-snap directory, you can get it e.g. from [Pling store](https://www.gnome-look.org/p/1665694/)

```sh
git clone git@github.com:stoefelz/arcaurora-cursors-snap.git
cd arcaurora-cursors-snap
# copy now the zip file containing the cursors into this directory

snapcraft

# where CURRENT is the latest version of arcaurora-cursors
# and --dangerous since this local snap hasn't been verified
snap install arcaurora-cursors_CURRENT_amd64.snap --dangerous
```

## Applying the theme

In order to work, the snap package needs to have a '[plug](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)' 
available for 'icon-themes'.

To apply the theme to a single application, perform the following:

```bash
sudo snap connect [snap-you-want-to-theme]:icon-themes arcaurora-cursors:icon-themes
```

To apply to all applications run the following command. Thanks to @flexiondotorg for the handy loop.

```bash
for plug in $(snap connections | grep gtk-common-themes:icon-themes | awk '{print $2}'); do sudo snap connect ${plug} arcaurora-cursors:icon-themes; done
```

*NOTE*: Some apps like the Ubuntu Snap Store may require logging out, and back in to load the changes.
