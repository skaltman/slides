Scoped verbs
================

## Suffixes

| suffix | use when                                                         |
| :----- | :--------------------------------------------------------------- |
| \_all  | you want to apply the verb to all columns                        |
| \_at   | you want to apply the verb to specified columns                  |
| \_if   | you want to apply the verb to all the columns with some property |

## Examples

### `mutate()`, `summarize()`, `select()`, and `rename()`

#### Named functions

| Verb           | Example                                | Example explanation                                                                   |
| :------------- | :------------------------------------- | :------------------------------------------------------------------------------------ |
| summarize\_all | summarize\_all(mean)                   | finds the mean of all variables                                                       |
| summarize\_at  | summarize\_at(vars(x, y), mean)        | finds the mean of variables x and y                                                   |
| summarize\_if  | summarize\_if(is.double, mean)         | finds the mean of all double variables                                                |
|                |                                        |                                                                                       |
| mutate\_all    | mutate\_all(as.character)              | converts all variables to characters                                                  |
| mutate\_at     | mutate\_at(vars(x, y), as.character)   | converts variables x and y to characters                                              |
| mutate\_if     | mutate\_if(is.factor, as.character)    | converts all factor variables to characters                                           |
|                |                                        |                                                                                       |
| rename\_all    | rename\_all(str\_to\_lower)            | changes all column names to lowercase                                                 |
| rename\_at     | rename\_at(vars(X, Y), str\_to\_lower) | changes the names of columns X and Y to x and y                                       |
| rename\_if     | rename\_if(is.double, str\_to\_lower)  | changes the names of double columns to lowercase                                      |
|                |                                        |                                                                                       |
| select\_all    | select\_all(str\_to\_lower)            | selects all columns and changs their names to lowercase (better to use rename\_all()) |
| select\_at     | select\_at(vars(X, Y), str\_to\_lower) | selects just columns X and Y and changes their names to x and y                       |
| select\_if     | select\_if(is.double, str\_to\_lower)  | selects just double columns and changes their names to lowercase                      |

#### Extra arguments

| verb           | example                                        | example\_explanation                                                                                                           |
| :------------- | :--------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| summarise\_if  | summarize\_if(is.double, mean, na.rm = TRUE)   | finds the mean, excluding NAs, of all double variables                                                                         |
| summarize\_all | summarize\_all(mean, trim = 0.1, na.rm = TRUE) | finds the mean of all variables, exluding NAs. Removes the bottom and top 10% of values of each variable before computing mean |

#### Anonymous functions

| verb           | example                           | example\_explanation                                       |
| :------------- | :-------------------------------- | :--------------------------------------------------------- |
| summarize\_all | summarize\_all(~ sum(is.na(.)))   | determines the number of NAs in each column                |
| select\_if     | select\_if(~ n\_distinct(.) \> 1) | selects only the columns with more than one distinct value |

### `filter()`

| verb        | example                                      | example\_explanation                                    |
| :---------- | :------------------------------------------- | :------------------------------------------------------ |
| filter\_all | filter\_all(all\_vars(\!is.na(.))            | finds rows without any NAs                              |
| filter\_all | filter\_all(any\_vars(\!is.na(.))            | finds rows with at least one non-NA value               |
|             |                                              |                                                         |
| filter\_at  | filter\_at(vars(x, y), all\_vars(\!is.na(.)) | finds rows where both x and y are non-NA                |
| filter\_at  | filter\_at(vars(x, y), any\_vars(\!is.na(.)) | finds rows where at least one of x and y is non-NA      |
|             |                                              |                                                         |
| filter\_if  | filter\_if(is.double, all\_vars(\!Is.na(.))  | finds rows where all double variables are non-NA        |
| filter\_if  | filter\_if(is.double, any\_vars(\!Is.na(.))  | finds rows where at least one double variable is non-NA |
