## Datasets

### Ednet

- KT1: 5.6GB, since April 2017, questions come in bundles, can use DKT or self-attentive KT for this. 

  1. timestamp
  2. solving_id: learning session of student corresponding to bundle id, an integer starting from 1
  3. question_id: in form q{int}
  4. user_answer: a character between 'a' and 'd'
  5. elapsed_time: the time spent on the question (in miliseconds)

  | timestamp     | question\_id | bundle\_id | user\_answer | elapsed\_time |
  | ------------- | ------------ | ---------- | ------------ | ------------- |
  | 1548996377530 | 48           | q2844      | d            | 47000         |
  | 1548996378149 | 48           | q2845      | d            | 47000         |
  | 1548996378665 | 48           | q2846      | d            | 47000         |
  | 1548996671661 | 49           | q4353      | c            | 67000         |
  | 1548996787866 | 50           | q3944      | a            | 54000         |

  

- KT2: 3.1GB, since Auguest 2018, added action sequences. In addition to the above, it has

  1. action_type: either 'enter': opening a question, 'respond': choosing an answer, or 'submit': final choice
  2. item_id
  3. source: where the material is accessed
     1. sprint: students chooses a subject and only answers questions for that
     2. tutor:  students solve a series of recommended questions
     3. in_review: students solve questions that they have solved before
     4. adaptive_offer: students answer a new set of questions because they got many wrong answers
     5. todays_recommendation: in form of sprint or review_quiz, recommended daily
  4. platform: either 'mobile' or 'web'

  | timestamp     | action\_type | item\_id | source    | user\_answer | platform |
  | ------------- | ------------ | -------- | --------- | ------------ | -------- |
  | 1358114668713 | enter        | b4957    | diagnosis |              | mobile   |
  | 1358114691713 | respond      | q6425    | diagnosis | c            | mobile   |
  | 1358114701104 | respond      | q6425    | diagnosis | d            | mobile   |
  | 1358114712364 | submit       | b4957    | diagnosis |              | mobile   |
  | 1358114729868 | enter        | b5180    | sprint    |              | mobile   |
  | 1358114745592 | respond      | q6815    | sprint    | c            | mobile   |
  | 1358114748023 | respond      | q6816    | sprint    | a            | mobile   |
  | 1358114748781 | respond      | q6814    | sprint    | a            | mobile   |
  | 1358114751032 | submit       | b5180    | sprint    |              | mobile   |

  

- KT3: 4.3GB, cause students might do other stuff when doing the questions

  1. action_type: also has 'quit' now

- KT4: 6.4GB, supports even more action types

- Contents: questions, lectures, payment items, coupons, and scores.



### RIIID competition

- train.csv
  1. row_id
  2. timestamp: the time between user interaction and first event completion
  3. user_id
  4. content_id: id code for the user interaction
  5. content_type_id: '0' for question, '1' for watching a lecture
  6. task_container_id: id code for batch of questions or lectures.
  7. user_answer: could be '-1', '0', or '1', -1 is null for lectures
  8. answered_correctly: could be '-1', '0', or '1', -1 is null for lectures
  9. prior_question_elapsed_time: average time to complete the last bundle (without videos)
  10. prior_question_had_explanation: whether or not user saw the correct answer or an explanation to the last bundle.
- questions.csv
  1. question_id: corresponds to content_id for content_type_id == 0
  2. bundlue_id
  3. correct_answer
  4. part: corresponds to TOEIC format
     1. photographs
     2. Question-response
     3. Conversations
     4. Talks
     5. Incomplete sentences
     6. Text completion
     7. Single or multiple passages
  5. tags: the meaning is private but can be used for **clustering**
- lectures.csv
  1. lecture_id: corresponds to content_id for content_type_id == 1
  2. tag: the meaning is private but can be used for **clustering**
  3. part
  4. type_of: brief desc of the purpose of the lecture, could be 'concept', 'solving question', etc.
- example_test.csv: similar to test.csv but has the two below columns as well
  1. prior_group_responses: provides all of the user_answer entries in a string
  2. prior_group_answers_correct: provides all of the user_answer entries in a string
