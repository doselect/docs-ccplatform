## Machine Learning and Data Science

### Datasets
Problems can have any combination of the following datasets. You should upload the following datasets as zip archives.

#### Training dataset
This dataset will be available to the developers for training their model. It will be availabe at `/data/training/`.

#### Evaluation dataset
This dataset will be used to test the developer's solution. It will be available at `/data/test/`.

#### Sample dataset
This dataset will be available to the developers for validating their model before they submit for evaluation. It will also be available at `/data/test/`. Note that `/data/test/` will contain the sample datasets when the developer runs `sample` testcases.

### Available libraries in the environment
#### R
```
RCurl
dplyr
tidyr
readr
stringr
plyr
reshape2
lubridate
data.table
dtplyr
foreach
ggplot2
RColorBrewer
randomForest
rpart
ROCR
car
party
caret
mlr
tree
klaR
ipred
lars
penalized
```

#### Python
```
requests 2.12.0
simplejson 3.10.0
numpy 1.11.2
scipy 0.18.0
scikit-learn 0.18
matplotlib 1.5.3
cython 0.25.2
pandas 0.19.0
nltk 3.2
```

### Testcases
Testcases are programs which will be used to evaluate developer's submissions. You have freedom to write the testcases in `python 2`, `python 3` or `R`. The correctness of solution is determined by the exit status of the evaluation code. Evaluation code should exit with `zero` only if the submission is correct.

Sample testcases are used for self validation only and will not be used for final evaluation.

The evaluation code should write error metrics to the file `/code/errormetrics`.
```
SSE 2.45
RMSE 0.7
```

If you need to show plots in the reports, you can write the plots to `/code/output/` directory.
```R
output = read.csv("/code/prediction.csv")
png(filename = "/code/output/1.png")
plot(output$estimate)
dev.off()
```
