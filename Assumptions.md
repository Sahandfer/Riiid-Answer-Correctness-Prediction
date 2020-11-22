## Assumptions

1. Lectures and Questions are grouped by task_container_id and they can be mixed. We should try to explore the temporal dependencies between them.
2. Lectures cannot be just thrown out in the table and make the algorithm parse it. We should give it a special treatment like improving user heuristics (similar to how previous papers had user metadata like its knowledge)
3. Some people did previous data processing like getting a user distribution regarding its performance: % of correct answers, mean content accuracy, number of user answers
4. A new feature -> has watched a lecture about the topic and use this to model the influence of the lecture in the learning

## Assumptions

### True

1. The table is sorted for each user. Therefore, for each user, the first interaction has a *NaN* previous elapsed time and *None* Explanation.
2. Students get more correct answers the more time they spend on the platform.
3. Students get more correct answers the more questions they answer.
4. Students get more correct answers after seeing explanation
5. Students get more correct answers on some specific tags, since the number of answers per tag also matters.
6. Students are slightly more likely to get correct answers on some parts compared to others.
7. Students get more correct answers if they watch the lectures. 

### False

1. Task_container_id and bundle_id are the same (WRONG) --- Container is for the questions or lectures that the user sees before seeing the explanation of any of them. Bundle is a group of questions that are served together.
2. The time a student spends on the previous bundle affects the number of correct answers (MAYBE WRONG) --- eric's notebook showed that the average time for wrong and right answers is similar.
3. The more lectures the students watch, the more correct answers they get (PARTIALLY WRONG) --- since some people got more accuracy with less lectures.
4. Having a lecture in a batch helps --- batches without lectures had 8% more correct answers.

### To be investigated

1. Different type of lectures may have different effects
2. Students get more correct answers after seeing explanation.
3. Students get more correct answers after watching the lectures about the given topics.
4. There is a temporal dependancy between lectures and questions.