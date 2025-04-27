# Fusion

A public feedback board and roadmap system using GitHub Issues as the backend. Users can log in with GitHub, submit feedback, upvote ideas, view changelogs, and see the roadmap.

## Features

- **GitHub Authentication**: Log in with your GitHub account
- **Feedback Board**: Submit and view feedback items
- **Upvoting**: Upvote feedback items you support
- **Changelog**: View updates and changes
- **Roadmap**: See what's planned, in progress, and completed
- **Admin Controls**: Manage feedback items (for authorized users)

## Technology Stack

- HTML5 (semantic layout)
- TailwindCSS via CDN
- Vanilla JavaScript (no frameworks, no builds)
- GitHub REST API v3
- GitHub OAuth for authentication

## Setup Instructions

### Prerequisites

- GitHub account
- GitHub OAuth App registration

### GitHub OAuth App Registration

1. Go to your GitHub account settings
2. Navigate to Developer settings > OAuth Apps > New OAuth App
3. Fill in the following details:
   - Application name: Fusion Feedback (or your preferred name)
   - Homepage URL: `https://your-deployment-url.com` (or `http://localhost:3000` for local development)
   - Authorization callback URL: `https://your-deployment-url.com/callback.html` (or `http://localhost:3000/callback.html` for local development)
4. Register the application
5. Note down the Client ID
6. Generate a new Client Secret and note it down (you'll only see it once)

### Local Development

1. Clone this repository:
   ```bash
   git clone https://github.com/nhyyebo/fusion-feedback.git
   cd fusion-feedback
   ```

2. Create a `config.js` file in the `js` directory with your GitHub OAuth credentials:
   ```javascript
   const config = {
     clientId: 'YOUR_GITHUB_CLIENT_ID',
     redirectUri: 'http://localhost:3000/callback.html',
     owner: 'YOUR_GITHUB_USERNAME', // or organization name
     repo: 'fusion-feedback' // or your repository name
   };
   
   export default config;
   ```

3. Serve the project using a local web server. For example, using Python:
   ```bash
   # Python 3
   python -m http.server 3000
   ```
   Or using Node.js with a package like `http-server`:
   ```bash
   npx http-server -p 3000
   ```

4. Open your browser and navigate to `http://localhost:3000`

## Security Considerations

**Important**: This implementation uses the GitHub OAuth flow with a client-side application. For production use, consider implementing a server-side component to securely handle the OAuth flow and protect your client secret.

## License

MIT