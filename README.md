INSTALL

on linux, all the dependencies are probably available in your distro's repositories.

for linux:\
make sure you have the obs browser source and vlc media source available. they may need to be installed separately depending on how your distro packages obs. you should not use the obs flatpak as it's hard to install plugins on it.\
also you need to have ffmpeg installed with the proprietary media codecs, so you're able to decode the streamlink video.

install the dependencies:\
streamlink https://streamlink.github.io \
gradle https://gradle.org \
bun https://bun.com \
git https://git-scm.com \
git lfs https://git-lfs.com \
java 21+ (surely you can figure this out without a link)

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
$ git clone https://github.com/mirailuv/streamtool.git \
$ git clone https://github.com/Notava1ble/mcsr-obs-inv-displayer.git

set up streamtool following the instructions here:\
https://github.com/mirailuv/streamtool

set up inventory viewer:\
open terminal in the mcsr-obs-inv-displayer folder.\
rename .env.example to .env\
edit the file and change INPUT_FILE to be the path to the symlink you created for streamtool.\
run the install command:\
$ bun install\
then you can try to run it with:\
$ bun run start

copy the files in configfiles.\
copy config.twitch to streamlink config folder, on linux that would usually be ~/.config/streamlink/ \
create the folders if they don't exist.\
edit the file and add your twitch token. if you don't want to do this, you can also just remove the line from the config.

on linux, also copy discord-audio.conf to pipewire config folder, that would usually be ~/.config/pipewire/pipewire.conf.d/\
create the folders if they don't exist.\
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