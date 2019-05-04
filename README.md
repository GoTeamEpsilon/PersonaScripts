![IMG](./assets/images/banner.png)

### *desktop.yml - a solution for installing curated, persona-based software suites on Linux PCs*

## About

desktop.yml provides various types of computer users capable software on a fresh or existing install of Ubuntu Linux or related system (see [here](#install) for compatible systems). Browse the personas and their descriptions below to get an idea of the great software packages desktop.yml will install.

## Personas

🧑 **everyday-user.yml**

Installs Windows compatibility software, day-to-day utilities, cloud music players, social messengers, Slack, an antivirus solution, image editors, an office suite, note taking applications, and popular web browsers.

👩‍💻 **programmer.yml**

Installs source code and text editors, IDEs, scientific python, database tools, popular cloud CLI tools, compiliers, Docker, version control systems, diagramming tools, FTP and SSH tools, virtual machine managers, QA testing tools, and a multi-paned terminal emulator.
 
🎨 **artist.yml**

Installs animation editors, 3D object creators, photography workflows managers, graphical transcoders, raster painting tools, video editors, fractal generators, and color palette selectors.

🎼 **musician.yml**

Installs digital audio workstations, multi-track audio recorders, multimedia file converters, drum machines, multi-effect processors, DJing mixers, and scorewriters.

⚙️ **engineer.yml**

Installs diagramming tools, parametric 3D CAD modelers, mind-mapping tools, and an electrical 
circuit diagramming solution.

🎮 **gamer.yml**

Installs popular console and handheld emulators, PlayOnLinux, Steam, well-known Linux games, and gamer-specific communication and streaming platforms.

## Install

**Currently supported systems:**
- [Ubuntu 18.04](https://www.ubuntu.com/)
- [KUbuntu 18.04](https://kubuntu.org/)
- [XUbuntu 18.04](https://xubuntu.org/)
- [Ubuntu MATE 18.04](https://ubuntu-mate.org/)

*Install desktop.yml (line-by-line) like so:*

```
wget https://github.com/GoTeamEpsilon/desktop.yml/archive/master.zip
unzip master.zip
mv desktop.yml-master desktop.yml
rm master.zip
cd desktop.yml
sudo ./assets/install.sh
```

*With "sleep mode" turned off, install the personas like so:*

```
ansible-playbook -K -l localhost everyday-user.yml # Recommended for everyone
ansible-playbook -K -l localhost programmer.yml
ansible-playbook -K -l localhost artist.yml
ansible-playbook -K -l localhost musician.yml
ansible-playbook -K -l localhost engineer.yml
ansible-playbook -K -l localhost gamer.yml
```

___________

Note: If you are running the OS in a Virtual Machine, it is best to set the system clock as like so:

`sudo date --set "27 Jun 2014 1:17:00" && sudo apt update`

...Doing so will avoid `Updates for this repository will not be applied` installation errors.

## Technical

_PRs are welcomed to further add to the personas or create new ones!_

#### Notes:

  - desktop.yml is powered by [Ansible](https://www.ansible.com/) with [Snap](https://snapcraft.io/), [Apt](https://wiki.debian.org/Apt), [Pip3](https://pip.pypa.io/en/stable/), and [NPM](https://www.npmjs.com/) as the package managers.

  - No software configurations are included in this solution - the idea is that everyone will have different configurations, especially in the programmer persona.

  - To add Snap, Pip, Apt, and Npm Global tasks, view programmer.yml to see example of all of these in use.

  - To add bash tasks, explore musician.yml for a program called Giada. Look at the bash declaration and the corresponding script file in `./assets/scripts/musician/giada.sh` - Notice how the script checks for its existance and writes the program to `/usr/local/bin/` if it doesn't exist. Note that all scripts should write to `/usr/local/bin`.

  - The Snap module for Ansible is not production-ready at the time of this writing. As a result, the `command` function is used in place of a formal task declaration due to the lack of this module integration.

  - Avoid adding ppas targeted for older Ubuntu release

#### Unsupported Systems:

The Following Ubuntu-based systems do not work correctly with this solution. Below is a list of the OSes and the issue:

- LUbuntu 18.04 - Didn't install typical packages that are supplied by Bionic
- Zorin OS 12.4 - The installer keep yielding `could not get lock`, despite a fresh install
- Linux Mint 19.1 - Apt was pointing at "Tessa" release as opposed to Bionic, which lead to packages not being found

#### Top TODOs:

- [Consider ways to support systems that rely on Yum, Pacman, or RPM.](https://github.com/GoTeamEpsilon/desktop.yml/issues/53)

- [Simplify install process](https://github.com/GoTeamEpsilon/desktop.yml/issues/54)

- [Consider adding desktop entries + logos for /usr/local/bin programs](https://github.com/GoTeamEpsilon/desktop.yml/issues/55)

- [Add the following to programmer.yml: Latest Java JDK, Erlang, Elixir, Minikube, Dropbox, Swift, Wireshark](https://github.com/GoTeamEpsilon/desktop.yml/issues/57)

- [Add current user to the docker group to avoid having to use `sudo` for all commands](https://github.com/GoTeamEpsilon/desktop.yml/issues/60)

## Credits & License

[Team Epsilon](https://github.com/GoTeamEpsilon/purpose) is a volunteer team of like-minded developers who strive to positively contribute to open source through code, education, and kindness. [Join us](https://github.com/GoTeamEpsilon/purpose/issues/new). Support us on [Patreon](https://www.patreon.com/matthewvita).

_Project sub-team:_
- QA: [Dr. Andre Millet](https://github.com/andremillet)
- Code: [Matthew Vita](https://github.com/matthewvita)
- Code: [Victor Kofiav](https://github.com/kofiav)

Font Credit: Geo Sans Light

License: [Public Domain (CC0)](./assets/legal/LICENSE)
