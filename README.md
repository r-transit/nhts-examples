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

![data model](https://raw.githubusercontent.com/r-transit/nhts-examples/main/data_model.png)

```
library(tigris)
library(dplyr)
cbsas <- core_based_statistical_areas(class="sf", cb=TRUE)

hhs_by_cbsa <- dataset$data$household %>% 
  group_by(HH_CBSA) %>%
  summarise(count = n()) %>%
  right_join(cbsas, by = c("HH_CBSA" = "GEOID"))
```
