# EffectiveMass
A simple Python script used to calculate effective masses of electron and hole on valence and conduction bands automatically.

## Version
EffectiveMass v1.01

## Python Version
Python 3.6 or later.

## Installation
1. Move EffectiveMass to a directory where you can reach, and add EffectiveMass to $PATH variable in your system environment.
2. If you are running this script on Linux, you can chmod this script to make it executable.
3. Open command (CMD, Windows) or bash shell (Linux) and type the command below. It would echo "EffectiveMass v1.01" (i.e. the version of EffectiveMass) if it is successfully installed.
```Bash
# Windows
python EffectiveMass.py --version
# Linux
EffectiveMass.py --version
``` 

## Command
```bash
python EffectiveMass.py -p "project_directory" [-s "xsd_file"] [-c "bs_xcd_file"] [-h] [-v]
```
* This script would create a new file named "'project_name' Effective Mass.out" in the specified project directory, which contains the calculation results.
* Option "-p" (or "--project") is required to specify the project directory (i.e. "project_directory") which contains your calculated model file ("xsd_file") and band structure file ("bs_xcd_file").
* Options "-s" ("--xsd") and "-c" ("--xcd") are not essential if you don't change the project directory or file names. The default names of "xsd_file" and "bs_xcd_file" are "'project_name'.xsd" and "'project_name' BandStr.outmol" (under DMol3) (or "'project_name' Band Structure.xcd" (under CASTEP)), respectively.
* Options "-h" ("--help") and "-v" ("--version") are used to view the manuscript and check the version of EffectiveMass, respectively.

## Mechanism
The effective mass is calculated by![effective_mass](https://github.com/liujiacode/EffectiveMass/blob/master/figures/effective_mass.jpg).

## Attention
1. Currently only DMol3 and CASTEP codes in Materials Studio (MS) are supported.

2. Before running this script, you should calculate the band structure of a specified crystal model in MS first. The calculation directory (i.e. "project_directory") should be reachable and contains model file ("project_name".xsd) and band structure file ("project_name" Effective Mass.out, which could be generated by "Analysis - Band Structure").

3. Atom unit (a.u.) is used in this calculation, i.e. energy is in Ha (Hartree), effective mass is in me (free electron mass) and distance is in bohr. Don't worry about the conversion of unit, this script would do it automatically.

3. If the project directory or file names have been changed, you should specify the file names manually in calculation by using "-s" and "-c" options.

4. Derivatives in this script is calculated simply by:
    * 1 nd derivative: d_1 = (y_2 - y_1) / (x_2 - x_1)
    * 2 nd derivative: dd = (d_2 - d_1) / ((x_3 - x_1) / 2))
* without interpolation. So the results would be more accurate if **more band structure points (lower separations)** are calculated when performing **the DMol3 or CASTEP code (not this script)**. Also, you can calculate the derivatives by Origin or other softwares manually.
* The results calculated by Origin **might not** equal to the results calculated by this script because of different deriative-performing methods.

## Author
LiuJia

## Website
https://github.com/liujiacode/EffectiveMass

## License
This script is released under GPL v3.0 license.