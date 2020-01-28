01\_write-installed-packages.R
================
jprice
2020-01-27

``` r
## deja vu from earlier!

## create a data frame of your installed packages
## hint: installed.packages() is the function you need
pkgs <- as.data.frame(installed.packages())

## optional: select just some of the variables, such as
##   * Package
##   * LibPath
##   * Version
##   * Priority
##   * Built
pkgs <- pkgs[, c("Package", "LibPath", "Version", "Priority", "Built")]

## write this data frame to data/installed-packages.csv
## hint: readr::write_csv() or write.table()
## idea: try using here::here() to create the file path
write.csv(pkgs, here::here("data", "installed-packages.csv"))

## YES overwrite the file that is there now (or delete it first)
## that's a old result from me (Jenny)
## it an example of what yours should look like and where it should go

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
    ## loaded via a namespace (and not attached):
    ##  [1] Rcpp_1.0.3      here_0.1        digest_0.6.23   rprojroot_1.3-2
    ##  [5] backports_1.1.5 magrittr_1.5    evaluate_0.14   highr_0.8      
    ##  [9] rlang_0.4.3     stringi_1.4.5   rmarkdown_2.1   tools_3.6.2    
    ## [13] stringr_1.4.0   xfun_0.12       yaml_2.2.0      compiler_3.6.2 
    ## [17] htmltools_0.4.0 knitr_1.27
