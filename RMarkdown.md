# RMarkdown

This document contains notes, shortcuts, cheat-sheets, etc. pertaining to R Markdown.

#### Table of Contents
1. [Specify output location](#specify-output-location)

### Specify output location

When knitting a document from within RStudio, the output directory by default is set to the working directory of the script (i.e., where the script resides).
To redirect the output directory/file location from within an RMarkdown document, without calling knitr::knit() or rmarkdown::render(), we can define a new 
function to supercede the native render() that will specify the output path.

Place this function inside the Rmarkdown header, before the output section. This redefines the knitr command to specify the output directory/file. We can define
an directory only (in which case the markdown doc's filename will be used) or we can specify the full path with an output file.

``` r
---
knit: (function(inputFile, encoding) { 
      rmarkdown::render(inputFile,
                        encoding=encoding, 
                        output_file='C:/path/to/output/output.html')})
output:
  slidy_presentation: default
---
```

Of, to specify an output directory only: ```output_dir='C:/path/to/output' ```

Adapted from: https://stackoverflow.com/questions/28894515/rmarkdown-directing-output-file-into-a-directory
