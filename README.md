# nhts-examples
for loose examples around using NHTS survey data

```
install.packages('devtools')
devtools::install_github('Westat-Transportation/summarizeNHTS')
library(summarizeNHTS)
download_nhts_data("2017", exdir="~/Documents/data")
dataset <- read_data("2017", csv_path = "~/Documents/data")
statistic <- summarize_data(
  data = dataset,
  agg = "household_count",
  by = c("HHSIZE","HHVEHCNT")
)
make_chart(statistic)
```



