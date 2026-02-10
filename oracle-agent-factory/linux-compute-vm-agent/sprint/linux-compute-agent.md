# How do I create a Linux Compute/VM Agent?
**Estimated Time: 15 minutes**

## Introduction
![Compute Icon](images/icon-compute.png " ")

This sprint guides you through creating a **Linux Compute/VM Agent** using the Oracle Agent Factory. This agent enables you to manage and monitor Linux virtual machines using natural language.

**(Architecture Overview)**
![Oracle Agent Factory Architecture](images/architecture.png " ")

## Prerequisites
Before starting, ensure you have:
1.  **Set up the MCP Server**: The backend logic relies on a custom MCP server. If you haven't set this up, please follow the [MCP Server Setup LiveLab](#). (_Placeholder Link_)
    *   The backend logic (similar to `mcpserver.py` and `wayflowmcp.py`) must be running on your designated OCI VM.
2.  **Access to Oracle Agent Factory**: You must be logged into the Agent Factory console.

## Step 1: Open Oracle Agent Factory
Start from the **Agent Factory Home Screen**. This is your command center for building and managing intelligent agents.

![Agent Factory Home Screen](images/agent-factory-home.png " ")

## Step 2: Open Custom Flows and Create Flow
Navigate to the **"My custom flows"** section. You will see a list of existing flows. Click the **Create flow** button to start a new project.

![Create Flow Button](images/create-flow.png " ")

## Step 3: Blank Canvas
You will be presented with a **blank canvas**. This is where you can visually build your agent flow.

![Blank Canvas](images/blank-canvas.png " ")

## Step 4: Design the Agent Flow
Build the flow as shown in the screenshot below. This design empowers the agent to execute Linux CLI commands via the MCP server.

![Console Commander Flow](images/console-commander-flow.png " ")

### Logic Configuration
1.  **Chat Input**: Start with a **"Chat input"** node to capture the user's command.
2.  **MCP Server**: Add an **"MCP server"** node.
    *   **URL**: Set this to your MCP endpoint (e.g., `http://<your-mcp-server-ip>:8009/mcp`).
    *   **Auth**: Set to `None` (or as required by your setup).
3.  **Agent Node**: Add an **"Agent"** node and configure it:
    *   **Tools**: Connect the MCP Server node to the **"Tools"** input of the Agent.
    *   **Custom Instructions**:
        > "You are an assistant that can call tools from the 'ConsoleCommander' MCP server. Your job is to produce terminal-friendly dashboards, CLI visuals, and safe operational outputs for the user."
    *   **Model**: Select a capable model (e.g., Llama 3 or similar).
4.  **Chat Output**: Connect the Agent's output to a **"Chat output"** node to display the response.

## Step 5: Testing
1.  Click **Playground**.
2.  Try commands like:
    *   "Check disk usage on the server."
    *   "List running processes."
    *   "Show me the uptime."
    ![Playground Test](images/playground-test.png " ")

## Conclusion
You have created a **Linux Compute/VM Agent** capable of interacting with your infrastructure via a secure MCP gateway.

## Acknowledgements
*   **Author** - Lavkesh Singh
*   **Last Updated By/Date** - February 2026
