<p align="center">
  <img src="public/banner.png" alt="Autopilot Logo" width="200"/>
</p>

<h1 align="center">Autopilot - Using GPT to Work on Entire Codebases</h1>

<p align="center">
  <strong>Autopilot</strong> is an AI tool that utilizes GPT to read a codebase, create context, and solve tasks that you request.
</p>

<p align="center">
  <img src="public/demo.gif" alt="Autopilot Demo" width="800"/>
</p>

# How it works 
(Generated by autopilot)

```plaintext
Task: Create a diagram explaining what this project and the process

+----------------------+     +----------------------+     +----------------------+
|  User inputs TASK    |     |  Read summaries of   |     | Identify relevant    |
|                      | --->|  all the files in    | --->| files for the task   |
|                      |     |  codebase            |     | using GPT AI         |
+----------------------+     +----------------------+     +----------------------+
                                                       |
                                                       v
                                           +-----------------------+
                                           | Extract relevant       |
                                           | context from files     |
                                           | using GPT AI           |
                                           +-----------------------+
                                                       |
                                                       v
                                           +-----------------------+
                                           | Suggest changes based  |
                                           | on context & task      |
                                           | using GPT AI           |
                                           +-----------------------+
                                                       |
                                                       v
                                           +-----------------------+
                                           | Display suggested      |
                                           | changes to the user    |
                                           +-----------------------+
``` 

## Features

### CreateSummaries script:

- 📚 Pre-processes all the relavent code base files.
- 👀 A watcher continuously updates files that have been modified.

### 🖥️ UI script:

- 🧩 Desides what files to update for the given task.
- 🤖 Does code updates for you.
- 📋 Shows you what was updated. Full process log with each AI interaction also produced.
- 🔧 Optional interacrive mode to see the process and retry, continue, abort options.

## 🛠️ Installation

1. Clone the repository: `git clone https://github.com/fjrdomingues/autopilot.git`
2. Do `cd autopilot` to install dependencies: `npm install`
3. Create the `.env` file and set up the environment variables:
   1. Copy the .env.template file to .env: `cp .env.template .env`
   2. Set up an OpenAI API key and file with the key: `OPENAI_API_KEY=<your-api-key>`. [Create openAI API key](https://platform.openai.com/account/api-keys)
   3. Set the path to your code `CODE_DIR=<path-to-your-code>`
   4. Update `IGNORE_LIST=node_modules,coverage,public,__tests__`
   5. Update `FILE_EXTENSIONS_TO_PROCESS=.js,.tsx,.ts,.jsx`
   
## Running
### 1. The indexer
* `node createSummaryOfFiles --all` - creates a summary of all files (required for first run) and starts the watcher.
* `node createSummaryOfFiles` - starts the watcher for any code changes which would trigger a file re-index.
### 2. The tasker
* `node ui -t "YOUR_TASK"` - is the easiest way to start.
  * Solutions will be auto applied on your code and a git diff shown if possible. 
  * Alternatively you may specify `--auto-apply=false`.
* `node ui -h` - will show you all the options.

## Test/Interactive mode
This project is still in alpha stage. It's recommended that you use `node ui -i` for an interactive mode here you can review the output of every step before proceeding.

## Components

- **createSummaryOfFiles.js**: Manages the code summarization process for JavaScript and TypeScript files.
- **ui.js**: Handles the user interface (UI) interaction and utilizes the GPT-based summaries to complete tasks.

## 🤝 Contributing

We welcome contributions! Please submit pull requests to the repository, and ensure your changes align with the project's goals and guidelines. Together, we can make **Autopilot** an even more powerful and efficient tool for developers!
