## Impact Reporting

## Original version - from BSA 2021-2022 project
################################################################################
# Author: Lina Berbesi - Modified version based on original code from 2020 Cassie Zhang
# Project Changes : -  Additional Functions on tables and footnotes
#                   -  Function documentation with roxygen in .\man
#                   -  .Rprofile to load packages, functions and parameters used across the project
#                   -  Version Control in Github repository
#                   -  .gitignore file to avoid loading data
#                   -  integrate.r to re-run all chapters after being re factored
#                   -  renv.lock snapshot of packages and versions used in the project
# Peer Review : Cassie Zhang

# IMPORTANT MESSAGE:----------------------------------------------------------
# If the project needs to be share with someone else or run in a new machine 
# renv::restore() can be used to reinstall all the packages versions recorded in the lockfile

# clean R session environment -------------------------------------------------
if(exists(".keepers")) {rm(list=setdiff(ls(), .keepers))} else {rm(list=ls())}

# Loading required packages ----------------------------------------------------

# packages for loading other packages
require(pacman)
require(conflicted)

# packages for function documentation
require(roxygen2)

# packages for data consumption
require(readxl)
require(here)

# packages for processing data
require(dplyr)
require(tidyr)
require(stringr)
require(tidyverse)
require(janitor)
require(conflicted)
require(lubridate)

# packages for tables
require(stats)
require(table1)
require(flextable)
require(officer)
require(MASS)
require(gt)

# packages for visualizations
require(ggpubr)
require(ggplot2)
require(formattable)
require(gridExtra)
require(viridis)
require(scales)
require(patchwork)

# packages for formatting code
require(formatR) 

# packages for formatting word documents
require(officedown)

# packages to integrate with python (in the future)
require(hash)

# packages for direct age standardization
require(epitools)
require(surveil)

# packages for proportional/marginal age standardization
require(DirectStandardisation)

## Conflict resolution---------------------------------------------------------

conflicts_prefer(dplyr::filter(),  
                 dplyr::lag() , 
                 dplyr::select() ,
                 dplyr::combine(),
                 openxlsx::write.xlsx(), 
                 lubridate::year() , 
                 scales::percent(),
                 stats::chisq.test(),
                 flextable::compose(),
                 renv::load()
              )

## Loading Functions-----------------------------------------------------------

source(here("Auxiliary_Functions/Levels.R")) 
source(here("Auxiliary_Functions/Tables.R"))  
source(here("Auxiliary_Functions/Graphs.R")) 

## Reading data----------------------------------------------------------------


load(here("./Input/Impact_data_DecExtr.RData"))

## Flextable Defaults----------------------------------------------------------

set_flextable_defaults(
  theme_fun = theme_vanilla,
  big.mark = ",",
  font.size = 9,
  font.family = "Arial",
  padding.left = 2,
  padding.right = 2,
  padding.top = 0,
  padding.bottom = 0,
  table.layout = "autofit" 
  )

##  Footnotes Statements-------------------------------------------------------------------------------------------------

UnkString="Unknown/missing data excluded: "
 
RefSrcParent_label = ""  #"Screening Status"  #updated
BSATable_label = "Referral Source" #added

nonBSAString = "whose cancer was detected by non-BSA screening; the remainder were from other sources." 
 
histFootnote=stringr::str_wrap("Note: This figure contains Te Rēhita data after becoming national in 2020.", 120)
 
IQRStr="*IQR = Interquartile range"

nsstring="N/S Not shown due to small numbers in one or more subgroups"
 

## BSA report default template colors-------------------------------------------------------------------------------------

label_colour <- "#555B6C"
grid_colour <- "#AFDEDB"
BCF_colours <-c("#EE5999","#B0DEDC","#CACA8C","#303ea0","#4F5761","#CDA38C","#80D6F1","#FFF985","#888A8D","#C7CAE6")
BCF_text <-   c("#2e2926","#2e2926","#2e2926","#FFFFFF","#FFFFFF","#2e2926","#2e2926","#2e2926","#FFFFFF","#2e2926")

BSA_colours<-c("#274185", "#39BB9D", "#774092", "#58B0E3","#EE5999")
BSA_text<-c("#FFFFFF", "#2e2926","#FFFFFF","#2e2926", "#2e2926")


## Additional Information------------------------------------------------------------------------------------------------

# Flextable set up:
# Is this of any use: https://www.r-bloggers.com/2021/11/publication-ready-tables-with-flextable-and-own-theme-in-r/
# Following example from: https://ardata-fr.github.io/flextable-gallery/gallery/2022-06-16-tabulator/


