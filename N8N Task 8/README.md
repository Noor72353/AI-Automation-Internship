# Task 8: Custom MCP Server with AI Agent Integration

## Project Overview

This project demonstrates how to build and integrate a custom **Model Context Protocol (MCP) Server** with an AI Agent using n8n.

The project consists of two separate n8n workflows. The first workflow acts as an MCP Server and exposes external tools. The second workflow contains an AI Agent that connects to the MCP Server and uses its available tools to answer user queries.

The integration demonstrates how AI agents can interact with external tools through the Model Context Protocol (MCP).

## Project Objectives

- Understand the fundamentals of Model Context Protocol (MCP).
- Create a custom MCP Server using n8n.
- Expose multiple tools through an MCP Server Trigger.
- Connect an AI Agent to an MCP Server.
- Enable the AI Agent to select and execute tools based on user requests.
- Test tool execution and verify the returned results.

## Workflow Architecture

This project contains two independent n8n workflows that communicate through MCP.

### Workflow 1: MCP Server

**File:** `MCP Server.json`

This workflow acts as the tool provider. It uses the MCP Server Trigger node to expose tools to connected MCP clients.

**Components:**

1. **MCP Server Trigger**
   - Acts as the entry point for MCP connections.
   - Exposes the available tools to connected AI applications.
   - Allows MCP clients to discover and execute the registered tools.

2. **Wikipedia Tool**
   - Provides access to Wikipedia information.
   - Allows the AI Agent to retrieve information about topics, people, and other subjects.

3. **Calculator Tool**
   - Performs mathematical calculations.
   - Allows the AI Agent to execute arithmetic operations and return calculated results.

### Workflow 2: AI Agent Calling MCP

**File:** `AI Agent Calling MCP.json`

This workflow acts as the AI-powered MCP client.

**Components:**

1. **AI Agent**
   - Receives user questions and instructions.
   - Understands the user's request.
   - Determines which available tool is appropriate.
   - Uses the MCP connection to execute the selected tool.
   - Generates a response using the returned information.

2. **MCP Connection**
   - Connects the AI Agent to the custom MCP Server.
   - Provides access to the Wikipedia and Calculator tools.
   - Allows the AI Agent to discover and call available MCP tools.

## Architecture Diagram

```text
                  USER QUERY
                      |
                      v
        +----------------------------+
        |  Workflow 2                |
        |  AI Agent Calling MCP      |
        |                            |
        |        AI Agent            |
        +----------------------------+
                      |
                      | MCP Connection
                      |
                      v
        +----------------------------+
        |  Workflow 1                |
        |  MCP Server                |
        |                            |
        |    MCP Server Trigger      |
        |                            |
        |   +--------------------+   |
        |   | Wikipedia Tool     |   |
        |   +--------------------+   |
        |                            |
        |   +--------------------+   |
        |   | Calculator Tool    |   |
        |   +--------------------+   |
        +----------------------------+
                      |
                      v
               TOOL RESULTS
                      |
                      v
               AI AGENT RESPONSE
```

## Tools Implemented

| Tool | Functionality |
|---|---|
| Wikipedia | Retrieves information about requested topics. |
| Calculator | Performs mathematical calculations. |

## Testing and Results

Both tools were tested through the AI Agent in the second workflow.

### 1. Wikipedia Tool Test

The AI Agent was asked to retrieve information using Wikipedia.

**Result:** Successfully retrieved Wikipedia information through the MCP connection.

### 2. Calculator Tool Test

The AI Agent was asked to calculate the following expressions:

| Calculation | Expected Result |
|---|---:|
| 245 × 36 | 8,820 |
| 1250 ÷ 25 | 50 |
| (450 + 350) × 4 | 3,200 |
| 15% of 2400 | 360 |

**Result:** All four calculations returned the correct answers through the Calculator tool.

### Testing Summary

- MCP Server Trigger: Successfully configured.
- MCP connection: Successfully established.
- Wikipedia Tool: Successfully tested.
- Calculator Tool: Successfully tested.
- AI Agent: Successfully discovered and called the available tools.

## Technologies Used

- **n8n:** Workflow automation platform.
- **Model Context Protocol (MCP):** Standardized communication between AI applications and external tools.
- **AI Agent:** Interprets user queries and selects appropriate tools.
- **Wikipedia:** Information retrieval.
- **Calculator:** Mathematical computation.

## How It Works

1. The user submits a question to the AI Agent workflow.
2. The AI Agent analyzes the question.
3. The AI Agent identifies the appropriate tool.
4. The MCP connection communicates with the MCP Server workflow.
5. The MCP Server executes the selected tool.
6. The tool returns its result through the MCP connection.
7. The AI Agent uses the result to generate a response.

## Setup Instructions

1. Import `MCP Server.json` into n8n.
2. Configure the required tool settings and activate or run the MCP Server as appropriate for your n8n configuration.
3. Copy the MCP connection details from the MCP Server Trigger.
4. Import `AI Agent Calling MCP.json` into n8n.
5. Configure the MCP Client connection using the MCP Server connection details.
6. Configure the required AI model credentials.
7. Execute the AI Agent workflow and test the available tools.

**Note:** Imported workflows may require credentials and connection settings to be configured again in your n8n account.

## Security Notes

- Never upload API keys, access tokens, or private credentials to GitHub.
- Keep MCP connection URLs and authentication credentials private.
- Configure credentials securely in n8n.
- Review exported workflow JSON files before publishing them.

## Learning Outcomes

Through this project, I learned how to:

- Understand the Model Context Protocol architecture.
- Build a custom MCP Server in n8n.
- Expose multiple tools through an MCP Server Trigger.
- Connect an AI Agent to an MCP Server.
- Enable AI agents to discover and use external tools.
- Test tool execution and validate results.

## Project Status

**Completed and tested.**

Both the Wikipedia and Calculator tools were successfully tested through the AI Agent workflow.

## Author

**Noorwali Khan**

BS in Computer Science
FUUAST Islamabad, Pakistan

GitHub: [Noor72353](https://github.com/Noor72353)
