# Gemini Enterprise - Agents on Custom Surface

This project provides a proof-of-concept for integrating Gemini Enterprise agents into any web application, demonstrating how to bring the power of governed generative AI agents directly to users within their existing workflows.

This approach avoids forcing users to navigate to a separate Gemini Enterprise UI, promoting wider and more seamless adoption of agentic capabilities within a company.

More details can be found in [this article](https://medium.com/google-cloud/integrating-agents-on-custom-platforms-with-gemini-enterprise-04f8bb3b52ca).

## Concept

The core idea is to leverage the Gemini Enterprise API to interact with agents from a custom web interface. By calling the API, we can replicate the core functionalities of the Gemini Enterprise UI, such as listing available agents, managing conversation sessions, and exchanging messages with agents.

This allows developers to build custom user experiences for agents that are tailored to specific business processes and applications.

## Prerequisites

*   **Google Cloud Project:** An active Google Cloud Project with the Vertex AI API enabled.
*   **Gemini Enterprise Instance:** A configured Gemini Enterprise instance with agents and data sources.
*   **OAuth 2.0 Credentials:** An OAuth 2.0 Client ID for a web application to handle user authentication.

You will need the following information:
*   `PROJECT_ID`: Your Google Cloud project ID.
*   `PROJECT_NUMBER`: Your Google Cloud project number.
*   `LOCATION`: The region of your Gemini Enterprise instance.
*   `ENGINE`: The ID of your Gemini Enterprise engine.
*   `CLIENT_ID`: The OAuth 2.0 Client ID for your web application.

## Quick Start

1.  **Configure `index.html`**: Open the `index.html` file and fill in the placeholder values for `client_id`, `projectNumber`, `projectId`, `location`, and `engine` at the beginning of the `<script>` section.
2.  **Run a local web server**: You need to serve `index.html` from a web server. You cannot open it as a `file:///` URL because OAuth requires an authorized HTTP redirect URI. Most IDEs have a built-in web server for this purpose.
3.  **Authorize Redirect URI**: In your OAuth 2.0 Client ID configuration in Google Cloud Console, make sure to add the local address of your web server (e.g., `http://localhost:8080`) to the list of "Authorized redirect URIs".

## Usage

The `index.html` file demonstrates the following workflow:

1.  **Authentication**: The user authenticates using their Google account via an OAuth 2.0 flow.
2.  **Agent Selection**: The application lists the agents available to the authenticated user. The user can select an agent to interact with, or proceed without a specific agent to use the blended search over all connected data sources.
3.  **Conversation**: The user can send messages and receive responses from the selected agent or the blended search. The conversation history is maintained within a session.

### Session Continuity

A key feature of this approach is that the conversation session is managed by Gemini Enterprise. This means a conversation started in the custom web application can be seamlessly continued in the official Gemini Enterprise UI, and vice-versa.

## License

This library is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE).
# gemini-enterprise-custom-ui
