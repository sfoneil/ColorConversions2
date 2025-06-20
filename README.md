# ColorConversions2
Full update of old conversion functions. Now with 100% more OOP!
This is designed to be easier to make changes too while providing a more user-friendly interface. Not all functions are (or will be) replicated, but it should fit all major use cases. It also removes conflicts with existing Image Processing Toolbox functions.

## Create new color space objects with syntax

`newSpace = trivalue('SpaceName', [three trivalues], [luminance in cd/m^2]);`

e.g.

`myRGB = trivalue('RGB', [1 0 0], 20);`

Some spaces already have the luminance inherent so can be left off.

`myMW = trivalue('MW', [80 0 40]); % 40 candelas`


## Monitor calibration profiles (colorInfo2)

Monitor profiles measured with measureDisplay() can be loaded, otherwise a default will be used

`myRGB = trivalue('RGB', [1 1 1], 'CIName', 'BiosemiDPP_PR655.mat');`
colorInfo2 now has a bunch of redundant information but will be kept for the time being.

## To convert between spaces:

`XYZ = myRGB.convert('XYZ');`

The conversions now know where the starting space is.


## Creating spaces with custom options
Using 2/3 inputs uses default options (e.g. Stockman & Sharpe 2-degree), but these can be overridden with optional paired arguments:

`myRGB = trivalue('RGB', [1 0 0], 20, 'WhitePoint', 'C');`


## Other handy functions:
```
mySpace.changeoptions('WhitePoint', 'D50_2); % Changes an existing space to D50 2-degree

mySpace.changeoptions('ColorInfo2', 'AnotherMonitorProfile.mat'); % Changes calibrations when switching systems

Luv.reshapespace('tocylindrical'); % Converts Cartesian Luv to LCHuv
```
```
