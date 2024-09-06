# Discord Bot with MySQL Integration

This repository contains a Discord bot built using the `discord.py` library, integrated with a MySQL database, and hosted using Flask. The bot allows users to interact with a knowledge base of questions and answers through various Discord commands.

## Features

- **MySQL Integration**: Connects to a MySQL database to manage a knowledge base of questions and answers.
- **Interactive Commands**: Supports commands to ask questions, add new entries, update existing ones, and delete them.
- **Dynamic Matching**: Uses `difflib` to find and handle close matches for questions.
- **Web Hosting**: Includes a Flask-based hosting setup to keep the bot running.

## Setup

### Prerequisites

1. **MySQL Database**: Ensure that your MySQL server is running and the `batri9` database is set up with a `knowledge` table.
2. **Python**: Ensure you have Python 3.x installed.

### Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. **Install Dependencies**

   Install the required Python libraries using `pip`:

   ```bash
   pip install discord.py mysql-connector-python Flask
   ```

3. **Configure the Bot**

   - Open the `bot.py` file and replace the placeholder token in `bot.run()` with your actual Discord bot token.

   ```python
   bot.run('YOUR_DISCORD_BOT_TOKEN')
   ```

4. **Configure the MySQL Database**

   - Open the `bot.py` file and update the database connection details in the `connect_database` function:

   ```python
   def connect_database():
       return mysql.connector.connect(
           host="localhost",
           user="your_username",
           password="your_password",
           database="batri9"
       )
   ```

### Running the Bot

1. **Start the Hosting Server**

   The hosting server is set up using Flask to keep the bot running. Run the following command to start it:

   ```bash
   python hosting.py
   ```

2. **Start the Bot**

   In a separate terminal window, run the bot:

   ```bash
   python bot.py
   ```

## Commands

- **`! <question>`**: Ask a question. If the answer is not found, you can provide a new answer.
- **`!badel <question>`**: Update the answer for a given question.
- **`!fasa5 <question>`**: Completely delete a question from the database.
- **`!ref`**: Refresh the knowledge base data.

## Flask Hosting

The Flask server is configured to run on port 8081. It keeps the bot active by keeping the server running. The `hosting.py` file contains the following Flask setup:

```python
from flask import Flask
from threading import Thread

app = Flask(' ')

@app.route('/')
def home():
    return 'salem'

def run():
    app.run(host='0.0.0.0', port=8081)

def hosting():
    t = Thread(target=run)
    t.start()
```

## Notes

- Make sure to replace placeholders with your actual MySQL credentials and Discord bot token.
- The bot will need to be invited to your Discord server using the appropriate OAuth2 URL.

---
