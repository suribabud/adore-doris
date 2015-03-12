There are a few environment variables that ADORE uses to keep track of the settings, processes and folders. These variables are accessible with the `$variableName` format at the ADORE prompt.

# Variables: #

  * ADOREFOLDER
> This variable points to the ADORE installation folder. This variable is set during the initialization of ADORE.
  * projectFolder
> This variable points to the current project folder. It is best to set this variable to the full path. This variable is set using `settings init` command. Default:'.'
  * outputFolder
> This variable points to the current output folder. In interactive process it is suggested to use this as the current folder. ADORE scripts change this variable to make sure the outputs of multiple interferograms end up in the correct place. Default:'.'
  * processFolder
> This variable points to the current processing folder. Processing folder is the main directory for all radar processing and is the mother directory for runFolders. Default:'$projectFolder/process'
  * dataFolder
> This variable points to the current data folder. Data folder contains the data (or links to the data). Inside data folder each scene has its own folder. This folder is generated using `settings init` or `scenes init` commands. Default:'$projectFolder/data'
  * runName
> This variable holds the name for the current processing run. This allows for different processing attempts to be kept in the same project. Default: 'default'
  * runFolder
> This variable points to the current run folder. This is the mother directory for crop and interferogram (i12s) folders. Default:'$processFolder/$runName'
  * cropsFolder
> This variable points to the current crops folder. ADORE scripts place all scenes (crops) to this folder. Default:'$runFolder/crops'
  * i12sFolder
> This variable points to the current interferogram (i12s) folder. ADORE scripts place all interferograms inside this folder. Default:'$runFolder/i12s'
  * baselinesFolder
> This variable points to the baselines folder for the current run. The `baselines` command outputs all the files to this folder. Default:'$runFolder/baselines'
  * adoreHistoryFile
> This variable holds the location for the ADORE's history file. This file keeps the command history for ADORE. Default:'${projectFolder}/.history'
  * dorisVersion
> This variable holds the version of the DORIS, which determines the default input files (`*.drs`). This is determined during initialization.
  * master
> This variable holds the current master scene. Default is the first scene inside the data folder.
  * slave
> This variable holds the current slave scene. Default is the second scene inside the data folder.
  * dataFile
> This variable holds the pattern for the data file. This pattern is used to select the correct file inside the master and slave data folders. This setting is initialized using `settings init` or `scenes init`.
  * leaderFile
> This variable holds the pattern for the leader file. This pattern is used to select the correct file inside the master and slave data folders. This setting is initialized using `settings init` or `scenes init`.
  * volumeFile
> This variable holds the pattern for the volume file. This pattern is used to select the correct file inside the master and slave data folders. This setting is initialized using `settings init` or `scenes init`.
  * nullFile
> This variable holds the pattern for the null file. This pattern is used to select the correct file inside the master and slave data folders. This setting is initialized using `settings init` or `scenes init`.
  * rs\_az\_buffer
> This variable sets the default resampling azimuth buffer in pixels. If `rs_dbow` and `rs_dbow_geo` parameters are not set, slave is cropped a little smaller than the overlapping area estimated by orbits. Default:'200'
  * rs\_rg\_buffer
> This variable sets the default resampling range buffer in pixels. If `rs_dbow` and `rs_dbow_geo` parameters are not set, slave is cropped a little smaller than the overlapping area estimated by orbits. Default:'200'
  * slc\_rg\_res
> This variable holds the range resolution for the current processing. If not defined by the user it is estimated during `dem make` command to estimate the size of the image.
  * slc\_az\_res
> This variable holds the azimuth resolution for the current processing. If not defined by the user it is estimated during `dem make` command to estimate the size of the image. Automatic estimation of this parameter might be wrong for satellites other than Envisat, ERS-1, and ERS-2.
  * raster\_format
> This variable defines the output format for the `raster` command. If this is set to something other than `ras` (sunraster), imagemagick's `convert` utility is used to convert the image to the right format. Default:'ras'
  * bistatic
> This variable sets the environment for bistatic Tandem-X processing. It is checked at m\_crop, s\_crop and subtrrefpha steps to run the necessary processing for this product. When DORIS starts internally supporting this format, this variable will be deprecated. Default:'off'