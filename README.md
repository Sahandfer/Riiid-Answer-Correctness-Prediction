# Riiid! Answer Correctness Prediction

> This is the repository for our final project for the Advanced Machine Learning 2020 course at Tsinghua University.

## Repository Guide

```
├── Notebooks                       
│   ├── SAINT_training.ipynb   			# Training code for SAINT+
│   ├── SAKT_inference.ipynb   			# Inference code for SAKT
│   ├── SAINT_inference.ipynb   		# Inference code for SAINT
│   ├── SAINT_encoder_inference.ipynb   # Inference code for SAINT (encoder only)
├── Report.pdf                			# Final report for our project
```



## RIIID competition dataset

- **train.csv**
  1. row_id: unique id for the entry
  2. timestamp: the time between user interaction and first event completion
  3. user_id: the user related to this interaction.
  4. content_id: id code for the user interaction (used for ref)
  5. content_type_id: '0' for question, '1' for watching a lecture
  6. task_container_id: id code for container of questions/lectures.
  7. user_answer: could be 0-3, -1 is null for lectures
  8. answered_correctly: could be '-1', '0', or '1', -1 is null for lectures
  9. prior_question_elapsed_time: average time to complete the last container (without watching lectures)
  10. prior_question_had_explanation: whether or not user saw the correct answers or an explanation to the last container.
- **questions.csv**
  1. question_id: corresponds to content_id for content_type_id == 0
  2. bundle_id: the corresponding bundle
  3. correct_answer
  4. part: corresponds to TOEIC format
     1. 1-4 relates to listening tasks.
     2. 5-8 relates to reading tasks.
  5. tags: can be one or more.
- **lectures.csv**
  1. lecture_id: corresponds to content_id for content_type_id == 1
  2. tag: can only be one.
  3. part: corresponds to TOEIC format
     1. 1-4 relates to listening tasks.
     2. 5-8 relates to reading tasks.
  4. type_of: brief desc of the purpose of the lecture, could be 'concept', 'solving question', etc.
- **example_test.csv**: similar to test.csv but has the two below columns as well
  1. prior_group_responses: provides all of the user_answer entries in a string
  2. prior_group_answers_correct: provides all of the user_answer entries in a string



### Data Analysis

**train.csv**

1. There are *101,230,332* entries: *99,271,300* questions and *1,959,032* lectures.
2. There are *13,782* unique content IDs: *13,523* questions and *259* lectures.
3. There are *10,000* unqiue containers.
4. There are *393,656* unique users.
5. *Timestamp* is relative to each user.
6. **useless columns**: user_answer, row_id

**Questions.csv**

1. There are *13,523* entries.
2. There are *9,765* bundles, a bundle has at most *5* questions and at least *1* question. 
3. There are *188* tags,  *one question without a tag*.
4. There are *8* parts, *4* Listening and *4* Reading.
5. **useless columns**: correct_answer

**Lectures.csv**

1. There are *418* entries.
2. There are *151* different tags, a tag has at most *7* lectures and at least *1* lecture.

