Frequently asked questions.

# FAQ #
**How do I run multiple processing steps?**
> Separate commands with semicolon (`;`). Ex: `m_readfiles;m_porbits;m_crop;m_simamp`

**Does ADORE have tab completion?**
> ~~So far only the variable completion (`$m_res[tab]` completes to `$m_resfile`) and path completion is working.~~
> Yes! With [r121](https://code.google.com/p/adore-doris/source/detail?r=121) tab completion was introduced. You can do things like:
|`setti<TAB>` | will complete to settings |
|:------------|:--------------------------|
|`settings <TAB><TAB>`| will show available commands `apply  check  clear  fix    init   load   raw    reset  save`|
|`settings apply -r mas<TAB>`| will complete the word "master"|

**How do I remove existing results?**
> There is a command called `undo` to remove steps from result files. It can remove all steps after a given step (default action) or remove only a single step.

**How do I get a list of options the ADORE is using before running the step?**
> You can see what the Doris input files will be like using the show command. If you type `s coarsecorr` it will show you what adore thinks coarsecorr.drs should look like, without running the step.

**How do I create an initial settings file?**
> Command `settings init` will create an initial settings file by asking you several questions. Of course you can change any and every setting later on.

**Snaphu displays `Killed`, and does not produce any outputs. What is wrong?**
> It is probably due to low available memory and Linux is killing snaphu before it crashes the computer. If you are not using Linux, and if you have plenty of memory (>10xInterferogramSize) this is probably not the reason though.

**What are internal/external ADORE commands, functions, scripts?**
> Development of ADORE is built on different stages, and also includes different software and scripts developed previously, or for other software. To learn more about the differences, take a look at the wiki page [ADORE Functions and Scripts](adoreFunctionsAndScripts.md).

**Why does DEM make leave the some files (`.hgt,dds.cr.usgs.gov`) in the current folder?**
> The idea is to have a central DEM folder and keep all your DEM's in that folder. This way, having the `dds.cr.usgs.gov` file speeds up the initial indexing of the HTTP site. Also having the `.hgt files` may speed up your DEM generation if you create multiple DEM's using the same SRTM tiles, as they will not need to be re-downloaded.

**Why do I need to have the interferogram result file (`$i_resfile`) to create a DEM? Why can't it just grab the coordinates from the master result file?**
> The dem make script also requires to know the orbit incline which is reported by Doris in the coarse\_orbits step. Therefore dem make will only run after that step is completed.