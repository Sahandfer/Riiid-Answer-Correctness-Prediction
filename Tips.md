## Tips

1. Data analysis frameworks: https://www.kaggle.com/rohanrao/tutorial-on-reading-large-datasets/
2. "Finally got a competitive score with a sequential model -> 77.1 public lb. I am just glad the pipeline is working smooth. [@abdurrafae](https://www.kaggle.com/abdurrafae) It takes my pipeline about an hour + for inference on the entire test set as well" in answer to https://www.kaggle.com/c/riiid-test-answer-prediction/discussion/193276


## Data analysis

1. Transformers: someone used transformers and ignored students with 1500+ answers https://www.kaggle.com/claverru/demystifying-transformers-let-s-make-it-public
2. Lectures and Questions are grouped by task_container_id and they can be mixed. We should try to explore the temporal dependencies between them.
3. Lectures cannot be just thrown out in the table and make the algorithm parse it. We should give it a special treatment like improving user heuristics (similar to how previous papers had user metadata like its knowledge)
4. Some people did previous data processing like getting a user distribution regarding its performance: % of correct answers, mean content accuracy, number of user answers
5. A new feature -> has watched a lecture about the topic and use this to model the influence of the lecture in the learning

### TO-DO

- Check if all the task_container_id have the same order. If yes, then we can just pre-process the data more easily for all users. if we not to pre-process for each user
- Start implementing