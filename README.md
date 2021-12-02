
# **README on StereoConstantMethodsample**

<div>Created    : "2010-08-17 12:25:39 ban"</div>
<div>Last Update: "2021-12-02 22:58:35 ban"

**********

**StereoConstantMethodsample**


![StereoConstantMethodsample](imgs/StereoConstantMethodsample.png)  

**A sample stimulus presentation package for stereo vision psychophysics experiment (Constant method) in our research group**  

- This package contains a set of sample **MATLAB and Psychtoolbox-3 (PTB3)** scripts for Constant-method psychophysics experiment on 3D vision.
- It displays rectangular depth planes defined by binocular disparities (+/- arcmins) for testing psychophysical disparity discrimination acuity.
- This script should be run with MATLAB PTB3 ver 3.0.15 or above (not tested with pervious versions of PTB3 and PTB2).
- To estimate disparity discrimination thresholds, **psignifit** tool is used.
- Currently, you can run this sample only on Windows OS since the psignifit tool linked from this package is only compatible with Windows.
  To run this sample on Mac OSX and Linux boxes, you have to set psignifit tool so that it works properly on these machines. Then, please change the psignifit-related codes of *~/StereoConstantMethodsample/Presentation/StereoConstantMethodsample.m*.
- Before running the sample, please add a path to the psignifit executables to your 'PATH' environmental variable.
- ***Finally, this package is made publicly available in the hope of  keeping our research group being transparent and open. Furthermore, the package is made open also for people who are interested in our group's research activities, who want to join our group in the near future, and who want to learn how to create stereo stimuli for vision science.*** To these ends, I have tried to make the samples as simple as possible (but also as real as possible so as to be available in the real experiments in the form of what this package is) with omitting any kinds of hacking-like codes to compensate stimulus presentation timings etc. If you need such routines, please check the other stimulus presentation codes in my [**Retinotopy**](https://github.com/hiroshiban/retinotopy) repository etc.)

(Matlab is a registered trademark of [***The Mathworks Inc.*** ](https://www.mathworks.com/) )  

Thank you for using our software package.  
We are happy if StereoScreening can help your research projects.  

**Stimulus presentation and tasks**

The presentation will start by pressing the start button you defined as sparam.start_method.  
The package supports two types of tasks below.  

- **A-or-B task**  (when sparam.reference_disparity=NaN. For details, please see the description of the stimulusfile below)  
&nbsp;&nbsp; **Sequence:** *stim -- blank -- response -- stim -- blank -- response -- stim -- blank -- response ...*  
&nbsp;&nbsp; The task is to judge whether the target plane is near (closer to you compared to the fixational plane) or far.  
  - press key 1 or left-mouse-click when the stimulus is to near (key 1/2 are defined in the display file)  
  - press key 2 or right-mouse-click when the stimulus is to far.  

- **2 AFC(IFC)**  (when sparam.reference_disparity is set as to be a real value (reference arcmin))  
&nbsp;&nbsp; **Sequence:** *stim(or ref) - blank - stim(or ref) - blank - resp - stim(or ref) -blank -- stim(or ref) -- blank -- resp ...*  
&nbsp;&nbsp; The task is to judge which (the first or the second) of the two planes is near.  
  - press key 1 or left-mouse-click when the first stimulus is to near (key 1/2 are defined in the display file)  
  - press key 2 or right-mouse-click when the second stimulus is to near.  

For more details, please read the descriptions below.  
Also please check the header comments in ~/StereoScreening/Presentation/StereoScreening.m.  

**Acknowledgment**

The StereoConstantMethodsample package uses **Psychtoolboox** library for generating/presenting/controlling binocular disparity stimuli, and **Psignifit (mpsignifit)** tool for computing the subject discrimination thresholds and psychometric functions. We would like to express our sincere gratitude to the authors for sharing these great tools.  

**Psychtoolbox** : The individual Psychtoolbox core developers,  
            (c) 1996-2011, David Brainard  
            (c) 1996-2007, Denis Pelli, Allen Ingling  
            (c) 2005-2011, Mario Kleiner  
            Individual major contributors:  
            (c) 2006       Richard F. Murray  
            (c) 2008-2011  Diederick C. Niehorster  
            (c) 2008-2011  Tobias Wolf  
            [ref] [http://psychtoolbox.org/HomePage](http://psychtoolbox.org/HomePage)

**Psignifit** (**mpsignifit**): A free toolbox for psychometric function estimation.  
           Develped by Dr Ingo Frund, Dr Valentin Hanel and Dr Felix Wichmann.  
           [ref 1] [https://github.com/wichmann-lab/psignifit/wiki](https://github.com/wichmann-lab/psignifit/wiki)  
           [ref 2] [https://github.com/wichmann-lab/psignifit/archive/master.zip](https://github.com/wichmann-lab/psignifit/archive/master.zip)  

**How to run the script**

1. On the MATLAB shell, please change the working directory to  
   *~/StereoConstantMethodsample/Presentation/*  
2. Run the "***run_exp***" script as  

   ````MATLAB
   >> run_exp('subj_name',1); % this is a simple script that calls
   >>                         % StereoConstantMethodsample.m with
   >>                         % some condition files.
   ````

   Here, the first input variable is subject name or ID, such as 'HB' or 's01',  
   the second variable should be 1 or 2,  

For more details, please see the documents in *StereoConstantMethodsample.m*  
Also please see the parameter files in *~/StereoConstantMethodsample/Presentation/subj/_DEFAULT_*.  

For checking the routines of stimulus generations, please see  
*~/StereoConstantMethodsample/Generation* and *~/StereoConstantMethodsample/Common* directories.


**Usage**

```Matlab
function StereoConstantMethodsample(subjID,acq,:displayfile,:stimlusfile,:gamma_table,:overwrite_flg,:force_proceed_flag)
(: is optional)
```


**Example**

```Matlab
>> StereoConstantMethodsample('s01',1,'nf_display.m','nf_stimulus_exp1.m')
```


**Input variables**

<pre>
sujID         : ID of subject, string, such as 's01'
                !!!!!!!!!!!!!!!!!! IMPORTANT NOTE !!!!!!!!!!!!!!!!!!!!!!!!
                !!! if 'debug' (case insensitive) is included          !!!
                !!! in subjID string, this program runs as DEBUG mode; !!!
                !!! stimulus images are saved as *.png format at       !!!
                !!! ~/CurvatureShading/Presentation/images             !!!
                !!!!!!!!!!!!!!!!!! IMPORTANT NOTE !!!!!!!!!!!!!!!!!!!!!!!!
acq           : acquisition number (design file number),
                a integer, such as 1, 2, 3, ...
displayfile   : (optional) display condition file, such as 'shadow_display_fmri.m'
                as an example, please see ~/StereoConstantMethodsample/subjects/_DEFAULT_/nf_display.m
stimulusfile  : (optional) stimulus condition file, such as 'shadow_stimulus_exp1.m'
                all of the stimuli in this script are generated in real-time based on
                the parameters in the stimulus file. For details, please see this
                function and the other function in ../Generation and ../Common directries.
                as an example, please see ~/StereoConstantMethodsample/subjects/_DEFAULT_/nf_stimulus.m
gamma_table   : (optional) table(s) of gamma-corrected video input values (Color LookupTable).
                256(8-bits) x 3(RGB) x 1(or 2,3,... when using multiple displays) matrix
                or a *.mat file specified with a relative path format. e.g. '/gamma_table/gamma1.mat'
                The *.mat should include a variable named "gamma_table" consists of a 256x3xN matrix.
                if you use multiple (more than 1) displays and set a 256x3x1 gamma-table, the same
                table will be applied to all displays. if the number of displays and gamma tables
                are different (e.g. you have 3 displays and 256x3x!2! gamma-tables), the last
                gamma_table will be applied to the second and third displays.
                if empty, normalized gamma table (repmat(linspace(0.0,1.0,256),3,1)) will be applied.
overwrite_flg : (optional) whether overwriting pre-existing result file. if 1, the previous result
                file with the same acquisition number will be overwritten by the previous one.
                if 0, the existing file will be backed-up by adding a prefix '_old' at the tail
                of the file. 0 by default.
force_proceed_flag : (optional) whether proceeding stimulus presentatin without waiting for
                the experimenter response (e.g. presesing the ENTER key) or a trigger.
                if 1, the stimulus presentation will be automatically carried on.

NOTE:
displayfile & stimulusfile should be located at
~/StereoConstantMethodsample/Presentation/subjects/(subjID)/, like
~/StereoConstantMethodsample/Presentation/subjects/(subjID)/nearfar_display.m
~/StereoConstantMethodsample/Presentation/subjects/(subjID)/
</pre>


**Output variable and result file** 

<pre>
no output variable. the results (stimulus presentation timings, participant responses) are saved in
~/StereoConstantMethodsample/Presentation/subjects/(subjID)/results/(today)
as (subjID)_StereoConstantMethodsample_results_run_(run_num).mat.
</pre>


**Details of displayfile**

An example of "displayfile":  

<pre>
% ************************************************************
% This is the display file for StereoConstantMethodsample
% Please change the parameters below.
% MotionParallaxConstant.m
% Programmed by Hiroshi Ban   Aug 24 2015
% ************************************************************

% display mode, one of "mono", "dual", "dualcross", "dualparallel",
% "cross", "parallel", "redgreen", "greenred", "redblue", "bluered",
% "shutter", "topbottom", "bottomtop", "interleavedline",
% "interleavedcolumn", "propixxmono", "propixxstereo"
dparam.ExpMode='shutter';%'cross';

% screen ID, generally 0 for a single display setup, 1 for dual display setup
dparam.scrID=1;

% a method to start stimulus presentation
% 0:ENTER/SPACE, 1:Left-mouse button, 2:the first MR trigger pulse (simulated key press),
% 3:waiting for a MR trigger pulse, checking onset of pin #11 of the parallel port,
% or 4:custom key trigger (wait for a key input that you specify as tgt_key).
dparam.start_method=1;

% a pseudo trigger key from the MR scanner when it starts,
% only valid when dparam.start_method=4;
dparam.custom_trigger=KbName(84);

% keyboard settings
dparam.Key1=37; % key 1 = near
dparam.Key2=39; % key 2 = far

% whether giving correct/incorrect feedback
% 0 = no feedback, 1 = giving correct (green fixation and high-tone sound) or
% incorrect(red fixation and low-tone sound) feedbacks
dparam.givefeedback=1;

% screen settings

% whether displaying the stimuli in full-screen mode or as is
% (the precise resolution), 'true' or 'false' (true)
dparam.fullscr=false;

% the resolution of the screen height
dparam.ScrHeight=1200;

% the resolution of the screen width
dparam.ScrWidth=1920;
</pre>


**Details of stimulusfile**

An example of "stimulusfile":  

<pre>
% ************************************************************
% This is the stimulus file for StereoConstantMethodsample
% Please change the parameters below.
% MotionParallaxConstant.m
% Programmed by Hiroshi Ban   Aug 24 2015
% ************************************************************

% "sparam" means "stimulus generation parameters"

%%% image size
sparam.outerRectFieldSize=[8,8]; % target stimulus size in deg, [row,col]
sparam.innerRectFieldSize=[4,4]; % target stimulus size in deg, [row,col]
sparam.gapRectFieldSize=[0,0];   % widths [row(top and bottom),col(right and left)]
                                 % of the gap between inner and outer rectangles in
                                 % deg (if 0, no gap).
                                 % gapRectFieldSize + innerRectFieldSize < outerRectFieldSize

%%% disparity magnitude(s)

% target base disparity in deg (if non-zero, the target plane is
% located to near/far side compared to the fixation plane)
sparam.base_disparity=0;

% target disparities in arcmin
sparam.disparity=[8,  4,  2,  1, 0.5, -0.5, -1, -2, -4, -8];

% when sparam.reference_disparity is NaN, the task is A-or-B-task in which
% participants have to judge whether the target is located to near or far,
% while, when this value is set to a specific disparity (arcmins), the task
% becomes 2AFC in which particpants have to judge which of the planes
% (the first or the second) is located to near.
sparam.reference_disparity=NaN;

%%% the number of trials for each stimulus condition
sparam.numTrials=30;

%%% RDS parameters
sparam.dotRadius=[0.05,0.05]; % radius of RDS's white/black ovals
sparam.dotDens=2; % deinsity of dot in RDS image (1-100)
sparam.colors=[255,0,128]; % RDS colors [dot1,dot2,background](0-255)
sparam.oversampling_ratio=2; % oversampling_ratio for fine scale RDS images, [val]

%%% RDS noise paramters
% when sparam.noise_mode='none' (no noise condition),
% all parameters related to noise are ignored.
% when sparam.noise_mode='anti' (anticorrelated (left/right dot
% colors are flipped) RDSs are presented), only sparam.noise_ratio
% is used in generating RDSs.
% when sparam.noise_mode='snr'  (noises are added in disparities),
% please set all the noise-related paramters carefully.

% one of 'none', 'anti', and 'snr'
sparam.noise_mode='none';

% percentage (0-100) of noises in the RDS, used when sparam.noise_mode='anti' or sparam.noise_mode='snr'
sparam.noise_ratio=30;

% noise mean in disparity (arcmin), used only when sparam.noise_mode='snr'
sparam.noise_mean=0;

% noise SD in disparity (arcmin), used only when sparam.noise_mode='snr'
sparam.noise_sd=5;

% one of 'add' and 'replace', used only when sparam.noise_mode='snr'
sparam.noise_method='add';

% stimulus display durations in msec

% initial fixation duration in msec
sparam.initial_fixation_time=1000;

%%% duration in msec for each condition
sparam.condition_duration=2000;

%%% duration in msec for simulus ON period for each trial, integer (1)
sparam.stim_on_duration=1000;

%%% duration in msec for each trial
sparam.BetweenDuration=500;

%%% fixation size & color
sparam.fixsize=24; % radius in pixels
sparam.fixlinesize=[12,2]; % [height,width] of the fixation line in pixel
sparam.fixcolor=[255,255,255];

%%% background color
sparam.bgcolor=[128,128,128];

%%% RGB for background patches
sparam.patch_size=[30,30];   % background patch size, [height,width] in pixels
sparam.patch_num=[20,20];    % the number of background patches along vertical and horizontal axis
sparam.patch_color1=[255,255,255]; % 1x3 matrices
sparam.patch_color2=[0,0,0];       % 1x3 matrices

%%% size parameters
run(fullfile(fileparts(mfilename('fullpath')),'sizeparams'));
%sparam.ipd=6.4;
%sparam.pix_per_cm=57.1429;
%sparam.vdist=65;
</pre>
