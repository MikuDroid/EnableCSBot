# EnableCSBot

Enable Bots on Counter-Strike 1.6 Steam / maybe Non-Steam? A Metamod module to enable CS Bot in Counter-Strike 1.6.

## Introduction

Whole script kanged from https://github.com/Arkshine/CSBotEnabler , also included Bot Menu from https://steamcommunity.com/sharedfiles/filedetails/?id=1725204346

__What are the difference?__
-Plug and play (i hope)
-Included Bot Menu so you don't have to use console for adjusting bot settings
-Included stock maps NAV

## Configuration

The only configuration of this module is a cvar which allows to precache radio sounds used by the bots. Located in :page_facing_up:`csbot_enabler/config.ini`:

```
// Precache all bot radio sounds.
// Please note:
//   BotChatter.db must be present.
//   Keep in mind that's about 487 files for ~10 Mo total to download.
//   Files are precached via the generic files buffer.
// -
// Default: "0"
csbot_precache_radio_sounds "0"
```

if you want to know what are the cvars and commands available for CS Bots, type in the server console:

```
cvarlist bot
cmdlist bot
```

## Installation

### Steps

1. Stop your server
2. Clone this repo or Download as zip 
4. Unzip the contents to :open_file_folder:`cstrike`
5. Open & add an entry in :page_facing_up:`metamod/plugins.ini`:
    <table>
        <tr>
            <td>Windows</td>
            <td>`win32 addons/csbot_enabler/csbot_enabler_mm.dll`</td>
        </tr>
        <tr>
            <td>Linux</td>
            <td>`linux addons/csbot_enabler/csbot_enabler_mm_i386.so`</td>
        </tr>
    </table>
6. Configure the cvar in :page_facing_up:`csbot_enabler/config.ini`
7. Start your server and enjoy.

### Expected files location

```
├─ addons
│   └─ csbot_enabler
│       ├─ config.cfg
│       ├─ csbot_enabler_mm.dll
│       └─ csbot_enabler_mm_i386.so
├─ sound
│   └─ radio
│       └─ bot
│           ├─ a.wav
│           ├─ a_bunch_of_them.wav
│           └─ ...
├─ BotChatter.db
└─ BotProfile.db
```


### Troubleshooting

To check if plugin is properly loaded, type in the server console: `meta list`.
You see something like:
```
meta list
Currently loaded plugins:
      description      stat pend  file              vers      src  load unlod
 [ 1] CS Bot Enabler   RUN   -    csbot_enabler_mm  v1.0.0    ini  ANY   ANY
```
Check the server log as well:
```
CS Bot Enabler v1.0.0
Status: Loaded.
```
- If you see nothing, this means `plugins.ini` of metamod has not been modified. See step 3 above.
- If you see `badf load`, make sure you did not do  a typo in `plugins.ini` of metamod. If not, then report the issue.
- If you see `RUN` but bots are not available, check the server log. It should give some message errors. This means likely memory path has failed. Keep in mind that it works only on HLDS build >= 5971. Report the issue if you have the right version.