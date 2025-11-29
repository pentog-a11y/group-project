library(readr)
library(dplyr)
library(mosaic)

ai_sample_final <-  read_csv("Data Management/ai_sample2_final.csv")
articles_clean1 <- read_csv("Data Management/articles_clean1.csv")


dim(ai_sample_final)
dim(articles_clean1)

summary(articles_clean1)

tally(~category, data=articles_clean1)
```

```{r}
merged_df1 <- ai_sample_final %>%
  inner_join(articles_clean1, by = "article_id")

# View the first few rows
head(merged_df1)

# Optional: save the merged output
write.csv(merged_df1, "merged_output.csv", row.names = FALSE)
