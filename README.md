## Project Overview

This project leverages CrewAI to create an automated system for researching and writing news articles on groundbreaking technologies. The system is composed of two agents: a Senior Researcher and a Writer. These agents collaborate to identify and narrate the latest trends in technology, specifically focusing on the topic of AI in healthcare.

## Components

### Agents

1. **Senior Researcher** (`news_researcher`):
   - **Role**: Uncover groundbreaking technologies in a specified topic.
   - **Goal**: Provide a detailed report on the identified technology trends.
   - **Backstory**: Driven by curiosity and innovation, eager to explore and share knowledge that could change the world.
   - **Tools**: Uses `SerperDevTool` for internet searching capabilities.
   - **LLM**: Utilizes `ChatGoogleGenerativeAI` with the gemini-1.5-flash model.

2. **Writer** (`news_writer`):
   - **Role**: Narrate compelling tech stories about the specified topic.
   - **Goal**: Craft engaging and informative articles.
   - **Backstory**: Simplifies complex topics into engaging narratives.
   - **Tools**: Uses `SerperDevTool` for internet searching capabilities.
   - **LLM**: Utilizes `ChatGoogleGenerativeAI` with the gemini-1.5-flash model.

### Tasks

1. **Research Task** (`research_task`):
   - **Description**: Identify the next big trend in the specified topic, focusing on pros and cons, market opportunities, and potential risks.
   - **Expected Output**: A comprehensive 3-paragraph report on the latest AI trends.
   - **Agent**: Assigned to the `news_researcher`.

2. **Writing Task** (`write_task`):
   - **Description**: Compose an insightful article on the specified topic, focusing on the latest trends and their industry impact.
   - **Expected Output**: A 4-paragraph article on the topic advancements, formatted in markdown.
   - **Agent**: Assigned to the `news_writer`.
   - **Output File**: `new-blog-post.md`

### Process

The `Crew` is configured to execute tasks sequentially, starting with the research task followed by the writing task. The process is initiated by calling `crew.kickoff` with a specified topic.

## Tools

### SerperDevTool

- A tool for internet searching capabilities, used by both agents.
- Initialized with an API key from `SERPER_API_KEY` environment variable.

### Language Model

- **ChatGoogleGenerativeAI**: Uses the gemini-1.5-flash model for both agents, configured with an API key from `GOOGLE_API_KEY` environment variable.

## Installation

1. Clone the repository.
2. Install the required packages by running:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file and add your API keys:
   ```env
   GOOGLE_API_KEY=your_google_api_key
   SERPER_API_KEY=your_serper_api_key
   ```

## Usage

1. Ensure all dependencies are installed and the `.env` file is configured with the appropriate API keys.
2. Run the script to start the task execution process:
   ```bash
   python crew.py
   ```
3. The result will be printed in the console, and the output article will be saved in `new-blog-post.md`.

## Files

- `agents.py`: Defines the agents used in the project.
- `crew.py`: Sets up the crew and initiates the task execution process.
- `task.py`: Defines the tasks assigned to the agents.
- `tools.py`: Initializes the tools used by the agents.
- `requirements.txt`: Lists the dependencies for the project.

## Conclusion

This project demonstrates how to use CrewAI to automate the process of researching and writing news articles on the latest technology trends. By utilizing advanced language models and internet search tools, the system can efficiently produce high-quality content on specified topics.
