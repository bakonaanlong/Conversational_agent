# LangChain Conversational AI with Memory

A Python implementation of a conversational AI chatbot that maintains conversation history across multiple interactions using LangChain and OpenAI's GPT-4o-mini model.

## Features

- **Persistent Conversation Memory**: Maintains context across multiple messages within a session
- **Session Management**: Supports multiple independent conversation sessions via session IDs
- **LangChain Integration**: Leverages LangChain's powerful abstractions for building AI applications
- **OpenAI GPT-4o-mini**: Uses efficient and cost-effective language model

## Prerequisites

- Python 3.8+
- OpenAI API key

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Install required dependencies:
```bash
pip install langchain-openai langchain python-dotenv
```

3. Create a `.env` file in the project root and add your OpenAI API key:
```
OPENAI_API_KEY=your_api_key_here
```

## Usage

Run the script:
```bash
python main.py
```

### Basic Example

```python
from langchain_openai import ChatOpenAI
from langchain_core.runnables.history import RunnableWithMessageHistory
from langchain.memory import ChatMessageHistory
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

# Initialize the chatbot
llm = ChatOpenAI(model="gpt-4o-mini", max_tokens=1000, temperature=0)

# Set up conversation with session ID
session_id = "user_123"

response = chain_with_history.invoke(
    {"input": "Hello! How are you?"},
    config={"configurable": {"session_id": session_id}}
)
print(response.content)
```

## How It Works

1. **Memory Store**: A dictionary-based store maintains separate conversation histories for each session ID
2. **Prompt Template**: Combines system instructions, conversation history, and user input
3. **Chain Processing**: The prompt is processed through the LLM while automatically managing conversation context
4. **History Management**: Each message (both user and AI) is automatically saved to the session's history

## Configuration

You can customize the chatbot behavior by modifying these parameters:

- `model`: Choose different OpenAI models (e.g., "gpt-4", "gpt-3.5-turbo")
- `max_tokens`: Maximum length of generated responses (default: 1000)
- `temperature`: Controls randomness (0 = deterministic, 1 = creative)

```python
llm = ChatOpenAI(
    model="gpt-4o-mini",
    max_tokens=1000,
    temperature=0
)
```

## Project Structure

```
.
├── main.py           # Main application file
├── .env              # Environment variables (API keys)
├── .gitignore        # Git ignore file
└── README.md         # This file
```

## Example Output

```
AI: Hello! I'm doing well, thank you for asking. How can I assist you today?
AI: Your previous message was "Hello! How are you?"

Conversation History:
human: Hello! How are you?
ai: Hello! I'm doing well, thank you for asking. How can I assist you today?
human: What was my previous message?
ai: Your previous message was "Hello! How are you?"
```

## Use Cases

- Customer support chatbots
- Virtual assistants
- Interactive learning applications
- Multi-user chat systems
- Conversational interfaces

## Dependencies

- `langchain-openai`: OpenAI integration for LangChain
- `langchain`: Framework for building LLM applications
- `python-dotenv`: Environment variable management

## Security Notes

- Never commit your `.env` file to version control
- Keep your OpenAI API key confidential
- Add `.env` to your `.gitignore` file

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Built with [LangChain](https://python.langchain.com/)
- Powered by [OpenAI](https://openai.com/)

## Support

For issues, questions, or contributions, please open an issue in the GitHub repository.
