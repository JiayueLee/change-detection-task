# Read me for Color Change Detection Task
written by Kirsten Adam, last updated 27 July 2017

## Required software
This code runs in MATLAB using Psychtoolbox (<http://psychtoolbox.org>). The task should be compatible with both Mac and PC - it was tested on an iMac running OS X El Capitan (10.11.6) and on a PC running Windows 7. 

## Setting up the code
Place the experiment script and the instructions file in a folder, and make sure this folder is on Matlab's path. Right now, the script is set up to create a folder called `Subject Data` within the current directory and save the data there. If you want the data to be saved elsewhere, you will need to update the experiment's main directory, `p.root`. 

## General notes
* This code will not let you over-write existing data-files with the same subject number. For practice that will not be saved, use the subject number "0". Only this subject number can be over-written. If you want to save multiple files for the same subject (e.g. multiple sessions) you will need to change how the files are named / saved. d
* To escape in the middle of a session, hit the "ESCAPE" button during the response screen. This will save all data up to the current trial. Otherwise, the data is only saved to the file at the end of each block of trials. 
 
## Common changes that need to be made 
* Many of the key settings are in the sub-function `getPreferences()`. For example, you might change the number of blocks, set sizes, or number of trials per block. Set Size and Change (0 or 1) are fully counterbalanced within each block using the matlab function `fullfact`. To calculate the number of trials per block, multiple the length of `prefs.setSizes`, `prefs.change`, and the desired number of repetitions, `prefs.nTrialsPerCondition`. To add a new condition to be counterbalanced within block, you can easily do so by adding it to `prefs.fullFactorialDesign`. 
* For debugging mode, you can create a smaller window by setting `p.windowed` to 1. For experiment mode, set `p.windowed` to 0. You can manually change the size of the debugging window with the variables `x_size` and `y_size`. 
* To toggle whether trials proceed automatically or are manually initiated with a spacebar press, change the variable `p.manually_initiate` (1 = manual, 0 = auto). I usually let trials proceed automatically for college students, but it might sometimes be necessary to manually initiate for younger participants / clinical populations. 
* You might want to adjust the size of the stimuli & the total area that stimuli can appear in depending on your monitor size & viewing distance. Stimulus size is controlled with `prefs.stimSize`. Area that stimuli can appear in is controlled with `win.foreRect = [ 0 0 xLength yLength]`. This bounding box is then centered around fixation. Be careful - If you make the bounding box TOO SMALL, the code will enter an endless loop trying to find enough positions that satisfy the minimum distance requirements for the pseudo-random placement of objects within the bounding box. 
* For Windows machines, the "task bar" will frequently pop up on top of the psychtoolbox window. To avoid this, you need to change the computer settings to  [auto-hide the task bar] (http://www.thewindowsclub.com/auto-hide-taskbar-windows). If this does not work for you, I have included a .mex file that will hide the taskbar at the beginning of the experiment and then un-hide it at the end. To use this mex file (`ShowHideWinTaskbarMex`), set the variable `p.manually_hide_taskbar` to 1.  
 