# Reddit Marketing Assistant Workflow

## Overview

<img src="https://github.com/user-attachments/assets/60276590-0b6e-4c57-9ad4-beabd65d4f20" style="width: 300px;" align="right" />This n8n workflow automates the process of identifying marketing-related needs from Reddit posts. It performs targeted searches on Reddit, analyzes post content for specific business challenges, and then suggests possible solutions. Finally, it compiles all data into a Google Sheet for team reference.

### Key Workflow Nodes and Functions

1. **Trigger**:
   - **Manual Trigger** or **Form Trigger**: Allows users to start the workflow manually or by submitting keywords via an n8n form. The form requires keyword input, which the workflow uses to search relevant posts on Reddit.

2. **Search Reddit**:
   - Searches for posts within the specified subreddit (e.g., `smallbusiness`) based on provided keywords. Collects posts that meet specific criteria, such as a minimum number of upvotes and recent creation dates (within the last 180 days).

3. **Post Evaluation and Filtering**:
   - **If Node**: Filters posts based on engagement level and content availability.
   - **Post Judge (AI Node)**: Uses an AI model to classify if a post discusses a marketing problem or service need.
   - **Filter Node**: Ensures that only relevant posts are retained based on AI classification.

4. **Data Processing and Structuring**:
   - **Format Post Data**: Structures Reddit post data, capturing details such as upvotes, creation date, URL, and original text.
   - **Mistral Cloud Chat Models**: Multiple AI nodes provide deeper analysis, including summarization, solution generation, and identification of the most relevant “low-hanging fruit” for the marketing team to address.

5. **Google Sheets Integration**:
   - Appends the curated and processed post data, along with AI-generated suggestions, to a Google Sheet for team reference. Each row includes columns such as the post’s original content, solution ideas, and a summary.

## Key AI Nodes and Logic

- **Post Judge and Solutions Provider**:
  - Leverages AI (e.g., OpenAI Mistral Model) to classify posts and generate potential marketing solutions. AI prompts are tailored to identify business challenges and suggest actionable marketing strategies.

- **Low Hanging Fruit Agent**:
  - Provides one actionable recommendation per post, focusing on easily implementable ideas that can offer quick wins for the business.

- **Merging and Summarization**:
  - Summarizes post content and merges data from different AI nodes, ensuring concise and usable information is saved to Google Sheets.

## Google Sheets Data Structure

Each entry in the Google Sheet includes:
- **Solution**: AI-generated suggestion for addressing the business challenge.
- **Original Post**: Reddit post content for reference.
- **URL**: Link to the Reddit post.
- **Date**: Date of the Reddit post.
- **Subreddit**: Subreddit name.
- **Summary**: Brief summary of the post content.
- **Low-Hanging Fruit**: Key recommendation for quick wins.

### API Integrations

- **Reddit API**: Searches for and retrieves relevant posts.
- **Mistral Cloud (Langchain)**: Provides AI-based analysis for content classification and suggestion generation.
- **Google Sheets API**: Writes the processed data and insights into Google Sheets.

## Usage

1. **Initialize the workflow** by filling the keyword form or clicking ‘Test workflow’ in n8n.
2. **Provide keywords** relevant to the type of business challenges you want to monitor on Reddit.
3. **View output** in the linked Google Sheet to review Reddit posts and associated marketing insights.

## Requirements

- **Reddit API Access** for retrieving post data.
- **Google Sheets API Credentials** to store data.
- **Mistral Cloud AI API** for text analysis and recommendation generation.
