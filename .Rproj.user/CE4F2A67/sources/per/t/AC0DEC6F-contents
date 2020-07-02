
if(!require("rio")) install.packages('rio', repos='http://cran.us.r-project.org')
if(!require("tidyverse")) install.packages('tidyverse', repos='http://cran.us.r-project.org')

library(rio)
library(tidyverse)

data <- import("https://raw.githubusercontent.com/CSHoggard/-tech-data/master/database.csv", na.strings=c(""), setclass = "tbl_df")

### stage one: inspection ###

View(data) ### view data
class(data) ### check class
nrow(data) ### number of rows
ncol(data) ### number of columns
names(data) ### call column names
head(data) ### call first few rows
str(data) ### call data structure

### stage two: data 'tidying'

cols <- c("CODE", "CONTEXT", "COUNTRY", "CONDITION", "ARTEFACT", "SUB_CATEGORY", "RECOVERY_METHOD", "CLASSIFICATION", "BP_ASSOCIATION", "TP_ASSOCIATION", "ABS_DATE_METHOD", "RELAT_DATE_METHOD", "RELAT_DATE_CHRONO", "RAW_MAT", "DORS_BLADE_PROF", "BLADE_DET", "BLADE_CURV", "DORSAL_PATTERN", "BULB_MORPH", "CONUS_FORM", "BUTT_MORPH", "BUTT_PREP_1", "BUTT_PREP_2", "CORE_MORPH", "PLAT_REJUV", "CORE_METHOD", "CORE_DIRECTIONALITY", "CORE_TABLET_REJUV", "CORE_FLAKE_REJUV", "CORE_FRONT_REJUV", "CORE_DIST_REJUV", "CORE_SIDE_REJUV", "ORIENTATION", "BURINATION", "MODEL_DATA") ### call the columns needing converting to factor
data[cols] <- lapply(data[cols], factor) ### convert above the factors

data_quant <- select(data, CODE, ARTEFACT, CONDITION, SUB_CATEGORY, CLASSIFICATION, WEIGHT, LENGTH, WIDTH, ELONGATION, THICKNESS, PLAT_DEPTH, CORE_LENGTH, CORE_WIDTH, CORE_ELONGATION, TCSA, TCSP, BURINATION)
data_qual  <- select(data, CODE, ARTEFACT, CONDITION, SUB_CATEGORY, CLASSIFICATION, DORS_BLADE_PROF, BLADE_DET, BLADE_CURV, DORSAL_PATTERN, BULB_MORPH, BUTT_PREP_1, BUTT_PREP_2, CORE_MORPH, PLAT_REJUV, CORE_METHOD, CORE_DIRECTIONALITY, CORE_TABLET_REJUV, CORE_FLAKE_REJUV, CORE_FRONT_REJUV, CORE_DIST_REJUV, CORE_SIDE_REJUV)

data_quant_bp <- select_if(data_quant, "ARTEFACT" == Backed Point)
