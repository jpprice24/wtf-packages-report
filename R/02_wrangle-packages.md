02\_wrangle-packages.R
================
jprice
2020-01-27

``` r
## remember to restart R here!
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
## create a data frame by reading from data/installed-packages.csv
## hint: readr::read_csv() or read.csv()
## idea: try using here::here() to create the file path
ipt <- read.csv(here::here("data", "installed-packages.csv"))

## filter out the base and recommended packages
## keep the variables Package and Built
## if you use dplyr, code like this will work:
apt <- ipt %>%
  filter(is.na(Priority)) %>%
  select(Package, Built)

## write this new, smaller data frame to data/add-on-packages.csv
## hint: readr::write_csv() or write.table()
## idea: try using here::here() to create the file path
write.csv(apt, here::here("data", "add-on-packages.csv"))


## make a frequency table of package by the version in Built
## if you use dplyr, code like this will work:
apt_freqtable <- apt %>%
  count(Built) %>%
  mutate(prop = n / sum(n))

## write this data frame to data/add-on-packages-freqtable.csv
## hint: readr::write_csv() or write.table()
## idea: try using here::here() to create the file path
write.csv(apt_freqtable, here::here("data", "add-on-packages-freqtable.csv"))

## YES overwrite the files that are there now
## they are old output from me (Jenny)
## they are just examples

sessionInfo()
```

    ## R version 3.6.2 (2019-12-12)
    ## Platform: x86_64-apple-darwin19.2.0 (64-bit)
    ## Running under: macOS Catalina 10.15.2
    ## 
    ## Matrix products: default
    ## BLAS/LAPACK: /usr/local/Cellar/openblas/0.3.7/lib/libopenblasp-r0.3.7.dylib
    ## 
    ## locale:
    ## [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8
    ## 
    ## attached base packages:
    ## [1] stats     graphics  grDevices utils     datasets  methods   base     
    ## 
    ## other attached packages:
    ## [1] dplyr_0.8.3
    ## 
    ## loaded via a namespace (and not attached):
    ##  [1] Rcpp_1.0.3       here_0.1         rprojroot_1.3-2  crayon_1.3.4    
    ##  [5] digest_0.6.23    assertthat_0.2.1 R6_2.4.1         backports_1.1.5 
    ##  [9] magrittr_1.5     evaluate_0.14    pillar_1.4.3     highr_0.8       
    ## [13] rlang_0.4.3      stringi_1.4.5    rmarkdown_2.1    tools_3.6.2     
    ## [17] stringr_1.4.0    glue_1.3.1       purrr_0.3.3      xfun_0.12       
    ## [21] yaml_2.2.0       compiler_3.6.2   pkgconfig_2.0.3  htmltools_0.4.0 
    ## [25] tidyselect_0.2.5 knitr_1.27       tibble_2.1.3
