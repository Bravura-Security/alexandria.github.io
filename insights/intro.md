---
title: Insights
nav_order: 5
---

# Insights

Insights are extracted from the knowledge held in our organization. Insights are extracted by applying a score card to content. So to have an insight you must have 

* Clearly identified content.
* A score card ( or rubric ) that content can be assessed against.

For example, a score card for a blog post could be

| Insight | Description | Scale |
|-----------|-------------|-------|
| Clarity | How clear is the blog post. Does it read well? | 1 (poor) - 5 (exceptional) |
| Accuracy | Are there factually incorrect items? | 1 ( yes, many) - 5 (none observed ) |
| Engagement | How well the content keeps the reader interested and encourages interaction. | 1 (low engagement) - 5 (highly engaging) |
|Relevance | How well the content addresses the needs and interests of the intended audience. |1 (off-target) - 5 (highly relevant) |

Below are currently implemented insights.

| Insight | Description | Scale |
|---------|-------------|--------|
| User session insights | Insights about how users are using alexandria | 1 (dangerous) - 5 (exceptional) | 
| Support ticket scoring | Score the overall quality of the customer support experience with helping to solve the issue | 1 (dangerous/inappropriate) - 5 (exceptional) | 
| Git commit scoring | Score the overall quality of git commits | 1 (dangerous code) -  5 (exceptional) | 
| Pull request scoring | Score the overall quality of pull requests | 1 (very poor) - 5 (exceptional) | 
| Aha idea scoring | Score the overall quality of aha ideas | 1 (very poor) - 5 (exceptional | 

If you have a have ideas for additional insights you would like to see generated please submit the idea to the [Idea Bank](https://alexandria-bravura-security.ideas.aha.io/).


# Configuring Insight Processing

Insights are configured on a book and tool level. The steps for doing this are:

1. Configure the [tool]((/alexandria.github.io/tools/intro)) so alexandria can speak to the remote system. 
1. Create a book that represents the area of the tool configured in 1 to analyze. For example, if you have activated the bitbucket tool, you can create books for each repository under your bitbucket account. 
1. Ensure the checkbox for "Analyze Book Content" is checked
1. Optional: Check Re-Analyze Book button if you want to immediately kick off the analysis phase. 

NOTE: because we are currently limited to a single tool of each type, each book is limited from content from a specific tool configuration. For example, you can configure a single bitbucket tool. Then have one or more books that target different areas of your bitbucket account. But you cannot target multiple bitbucket tenants concurrently.

# Insight processing

Insights are processed on a nightly basis. This is done through the following workflow

1. For each book in scope for analysis
1. List items that have been created or updated
1. For each item that has been created or updated, run the item against one or more score cards against

Each insight ( aka score card assessment ) counts twoards transaction counts for billing purposes. 

**NOTE:** we will be making score cards editable in a near term release of the solution.

