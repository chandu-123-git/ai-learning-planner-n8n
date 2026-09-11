# n8n AI Learning Path Automation

This repository contains an n8n workflow that uses an AI Agent to generate a structured learning path from a user's chat request.

The workflow researches the requested topic, creates a Google Docs document containing the learning plan, and schedules learning sessions in Google Calendar.

## Workflow

```text
When Chat Message Received
            ↓
         AI Agent
            │
            ├── Google Gemini Chat Model
            │
            ├── HTTP Request
            │      └── SerpAPI
            │
            ├── Create a Document in Google Docs
            │
            ├── Update a Document in Google Docs
            │
            └── Create an Event in Google Calendar
```

## How It Works

1. The user submits a learning request through the n8n chat interface.
2. The AI Agent interprets the request and determines the required actions.
3. Google Gemini generates the learning content and coordinates the tools.
4. The HTTP Request node retrieves relevant information through SerpAPI.
5. A Google Docs document is created.
6. The generated learning plan is added to or updated in the document.
7. Google Calendar events are created for the planned learning sessions.
8. The AI Agent returns a confirmation message to the user.

## Example Request

```text
Generate a 3-day learning path for Java.
```

## Example Result

The workflow can generate:

- A structured 3-day learning plan
- A Google Docs document containing the plan
- Google Calendar events for each learning session
- A final response containing the document link and scheduling status

Example response:

```text
Learning Path Complete!

Document: [Generated Google Docs URL]

Calendar: 3 events have been added to Google Calendar.

Your 3-day learning journey is ready!
```

## Requirements

Before importing and running the workflow, you need:

- n8n, either locally hosted or cloud-hosted
- A Google account
- Google Gemini API access
- A SerpAPI account and API key
- Google Docs access
- Google Calendar access

## Importing the Workflow

1. Open your n8n instance.
2. Create a new workflow.
3. Open the workflow menu.
4. Select **Import from File**.
5. Choose the workflow JSON file from this repository.
6. Configure the required credentials.
7. Review the node parameters and AI Agent instructions.
8. Test the workflow using the chat trigger.

## Credentials Configuration

The imported workflow may require you to configure or select your own credentials.

### Google Gemini

Configure a Google Gemini API credential in n8n using your Gemini API key.

### SerpAPI

Configure the HTTP Request node with your SerpAPI authentication details.

### Google Docs

Connect a Google Docs credential through Google OAuth and grant the required permissions.

### Google Calendar

Connect a Google Calendar credential through Google OAuth and select the calendar where learning events should be created.

## Repository Contents

```text
n8n-ai-learning-path-automation/
│
├── README.md
├── ai-learning-path-automation.json
└── workflow-overview.png
```

| File | Description |
|---|---|
| `README.md` | Documentation for the workflow |
| `ai-learning-path-automation.json` | Exported n8n workflow |
| `workflow-overview.png` | Screenshot of the workflow |

## Important Notes

- Credential configuration may be required after importing the workflow.
- Calendar start and end times must be valid.
- The selected Google Calendar must be accessible by the connected Google account.
- The workflow uses Google Gemini API usage, which may be subject to rate limits or quotas.
- The workflow currently focuses on generating learning paths, creating Google Docs documents, and scheduling Google Calendar events.
- Twitter/X integration is not included in this version.

## Security

Do not commit sensitive information to this repository.

Never upload:

- API keys
- OAuth client secrets
- Access tokens
- Refresh tokens
- Passwords
- Private credential exports

Store credentials using n8n's credential management system. If an API key is entered directly into a node, remove it before uploading the workflow to GitHub.

## License

This project is available for learning and personal use.
