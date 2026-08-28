INSTALL

on linux, all the dependencies are probably available in your distro's repositories.

install the dependencies:\
streamlink https://streamlink.github.io \
gradle https://gradle.org \
bun https://bun.com \
git https://git-scm.com \
git lfs https://git-lfs.com

on linux, you probably also want qpwgraph to configure audio.\
https://github.com/rncbc/qpwgraph

install obs plugins:\
gradient source https://obsproject.com/forum/resources/gradient-source.1172 \
tuna https://obsproject.com/forum/resources/tuna.843 \
waveform https://obsproject.com/forum/resources/waveform.1423

set up obs websocket. it should be enabled with port 4455 and authentication disabled.

decide where you want the setup folder to be, probably just home folder. open terminal in that folder.\
these are the commands for linux. if you're on windows the commands may be different.\
clone this repository. it may take a while as it's over 2GB download.\
$ git clone https://github.com/mirailuv/MCRL-Streaming.git \
enter the folder.\
$ cd MCRL-Streaming\
export the git lfs data.\
$ git lfs migrate export --include="*"\
clone the streamtool and inventory viewer repositories.\
$ git clone https://github.com/mirailuv/MCRL-Streaming.git \
$ git clone https://github.com/Notava1ble/mcsr-obs-inv-displayer.git

copy the files in configfiles.\
copy config.twitch to streamlink config folder, on linux that would usually be ~/.config/streamlink/
edit the file and add your twitch token. this isn't fully necessary but if you have turbo it'll prevent streams from cutting off due to ad breaks.

on linux, also copy discord-audio.conf to pipewire config folder, that would usually be ~/.config/pipewire/pipewire.conf.d/\
if the folders don't exist it should be fine to just create them.\
restart pipewire.\
$ systemctl --user restart pipewire\
open qpwgraph. the virtual output discord-audio should be there.\
open discord and start a mic test.\
the discord audio source will connect to your default audio output. connect it to discord-audio as well.\
press "Save" and enable "Activated".\
set up qpwgraph to run on startup.

open the file league.json with a text editor\
replace every instance of "/home/me/MCRL Streaming/" with the correct path to the folder.\
on windows, replace forward slashes in paths with backward slashes.\
open obs. click scene collections and import. find and select league.json as the file.\
make sure the audio inputs for mic and discord are correct.\
edit streamtool/obs_layout.json and set the correct paths there as well. also if you remade / renamed the audio sources, update the names.

that should be everything. you can test the streamtool using the files in testfiles.