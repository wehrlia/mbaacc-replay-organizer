# MBAACC Replay Organizer

A simple script that gives your MBAACC replays more descriptive names.

Turns this...

```
ReplayVS/
├── AKIHA_SxAOKO_240510124159.rep
├── AKIHA_SxAOKO_240510124334.rep
├── AKIHA_SxAOKO_240510124451.rep
├── AKIHA_SxAOKO_240510125515.rep
├── AKIHA_SxNANAYA_240510105121.rep
├── AKIHA_SxNANAYA_240510105255.rep
└── ...
```

Into this...

```
("s" is each player's score)
ReplayVS/
└── organized/
    ├── Alice/
    │   │   date and time (24h) nick1   char1     s nick2 char2    s
    │   ├── 2024-05-09-12-25-35,wehrlia,C-S.Akiha,0,Alice,C-Nanaya,2.rep
    │   ├── 2024-05-09-12-25-35,wehrlia,C-S.Akiha,0,Alice,C-Nanaya,2.rep
    │   ├── 2024-07-29-13-27-03,wehrlia,C-S.Akiha,1,Alice,C-Nanaya,2.rep
    │   └── ...
    ├── Bob/
    │   ├── 2024-02-08-11-06-00,wehrlia,C-S.Akiha,2,Bob,C-Nero,0.rep
    │   ├── 2024-03-08-15-07-56,wehrlia,C-S.Akiha,2,Bob,C-Nero,1.rep
    │   ├── 2024-03-09-17-09-20,wehrlia,C-S.Akiha,2,Bob,C-Nero,1.rep
    │   └── ...
    ├── Jane/
    │   ├── 2024-04-10-10-41-58,wehrlia,C-S.Akiha,1,Jane,F-Aoko,2.rep
    │   └── 2024-05-01-19-43-33,wehrlia,C-S.Akiha,0,Jane,F-Aoko,2.rep
    ├── John/
    │   └── 2024-01-20-11-10-59,wehrlia,C-S.Akiha,0,John,F-P.Ciel,2.rep
    └── localP1/ (local matches)
        └── 2023-12-23-18-04-51,localP2,C-S.Akiha,2,localP1,C-Nero,0.rep
```

Basically creating a folder called "organized" inside ReplayVS, then inside that folder, a separate folder for every person you've played against, each containing the actual replays, with new (and hopefully more cohesive) names.

Values are taken from `results.csv`, a file generated by CCCaster that makes a record of every match you've had.

DISCLAIMER: THIS SCRIPT WILL MOVE YOUR REPLAY FILES AROUND, AND GIVE THEM NEW NAMES. IF THAT CONCERNS YOU, BACKUP YOUR REPLAYS BEFORE RUNNING THIS SCRIPT. PLEASE. YOU HAVE BEEN WARNED.

# Requirements

- Any recent (past 2-3 years, maybe?) version of Python 3
- CCCaster v3.1

# Caveats

- Will probably not be very useful for replays of local matches, since the nicknames of each player will be "localP2" and "localP1".
- Won't work for replays of matches you spectated via CCCaster, since those matches aren't registered in the `results.csv` file. It will throw a warning and skip those replays.

# Installation and usage

1. Play your matches as usual;
2. After having played them, and having saved some replays, run the script. Instructions on how to install and run it are located below.

The replay files must be located inside the `ReplayVS` folder, and your `results.csv` file must be in the same folder as the script. None of the files should be modified directly in any way. If any of those conditions aren't met, the script will print an error message and exit, without modifying anything.

## Windows

Copy `organizer.bat` and `rep-organizer.py` to your MBAACC installation folder, then run `organizer.bat`:

You can also run the script from your terminal:

```
path\to\MBAACC> python rep-organizer.py
```

## Linux, \*BSD, or MacOS

Copy `rep-organizer.py` to your MBAACC installation folder, then run it from your terminal:

```bash
$ cd path/to/MBAACC/
$ python rep-organizer.py
```

You can also `chmod +x` it if you want.

# Guidelines for nicknames

1. Keep it ASCII, i.e no diacritics, CJK, Arabic, Hebrew, emojis, or any character from a language that isn't english.
2. Do not include any of the following characters in your nickname:  
`' " :`

Problematic characters will be excluded from folder and file names, since they can cause either encoding-related Python errors (in the case of non-ASCII characters), or various sorts of bugs inside MBAACC's replay selection menu.

For example, a nickname like `Bão demais falar: 'pão'` will become `Bo demais falar po`, etc.

# Licensing

This is public domain software. No warranty, provided "as is", etc. Do whatever you want with it. Giving credit is not mandatory, but appreciated.
