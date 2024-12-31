The competition dataset consists of user interactions from the [ChatBot Arena](https://lmarena.ai/) (formerly LMSYS). In each user interaction a judge provides one prompt to two different large language models and then indicates which of the models gave the more satisfactory response.

This is a [Code Competition](https://www.kaggle.com/c/wsdm-cup-multilingual-chatbot-arena/overview/code-requirements). When your submission is scored the example test data will be replaced with the full test set.

## Competition Phases and Data Updates

The competition will proceed in two phases:

1. A model training phase with a test set of historical data. This test set has about 10,000 rows.
2. A forecasting phase with a test set to be collected after the submission deadline. You should expect this test set to contain at most 25,000 rows. There may be fewer if that turns out to be necessary in order to maintain the schedule.

The Chatbot Arena team may release additional data during the model training phase.

## Files

**train.parquet**

- `id` - A unique string identifier for the row.
- `prompt` - The prompt that was given as an input to both models.
- `response_[a/b]` - The response from model_[a/b] to the given prompt.
- `winner` - The judge's selection. The ground truth target column.
- `model_[a/b]` - The identity of model_[a/b]. Only included in train.parquet.
- `language` - The language used in the prompt. Only included in train.parquet.
The visualization of this file is as below:

![[Train dataset sample.png]]

**test.parquet**

- `id` - A unique integer identifier for the row.
- `prompt`
- `response_[a/b]`
- `scored` - Whether or not the row is currently scored. During the model training phase this will be true for rows used for the public leaderboard; during the forecasting phase this will be true for rows used for the private leaderboard.
The visualization of this file is as below:

![[Test dataset sample.png]]

**sample_submission.csv** A submission file in the correct format.

- `id`
- `winner`

*Note that the dataset for this competition contains text that may be considered profane, vulgar, or offensive.*