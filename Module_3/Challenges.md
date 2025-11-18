# Overview

For the challenges in this module you will follow the general approach outlined below:

- Create a Braintrust dataset of 5-10 questions appropriate to the workflow being evaluated (you may augment it with Loop as appropriate, but be advised that Loop might not generate useful question-answer pairs for your workflow, so use them judiciously).
- Set the system prompt for the agent in the workflow to be "You are a helpful assistant."
- Run the workflow to obtain results as a Braintrust experiment.
- Create a scorer appropriate to the workflow.
- Run the scorer on the Braintrust experiment to obtain a baseline accuracy score.
- Update the system prompt and any other relevant parameters in the workflow to improve accuracy.
- Continue to make tweaks to your workflow, dataset, and scorer until you are satisfied with the accuracy score.
- Create a report summarizing your approach, the changes you made, and the starting and final accuracy score you achieved.  Copy and paste this report into the scorer when you are completed.  You will be scored based on the type and quality of improvements you made (overall workflow setup, prompts, datasets, scorers) and the improvement in the accuracy score from start to finish.  Be as detailed as possible.  

**Note:**
Be sure you report your accuracy scores as the average accuracy, reported as a percentage.


# Question 1

Take the workflow that you used in Module 1 Question 4 (the GitHub issues routing workflow).  Manually review the issues and come up with your own identification of which team they should be routed to.  These issue texts and your manual labels can then be used in your scorer.  Follow the above sequence to create a complete evaluation and report on its results.

# Question 2

Take the workflow that you used in Module 1 Question 5 (the Bill API docs RAG).  Follow the above sequence to create a complete evaluation and report on its results.

# Question 3

Take the workflow that you used in Module 2 Questions 6-8 (the SEC API extraction workflow).  Follow the above sequence to create a complete evaluation and report on its results.