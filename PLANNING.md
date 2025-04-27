# Fusion - Project Planning

## Project Overview
Fusion is a public feedback board and roadmap system using GitHub Issues as the backend. Users can log in with GitHub, submit feedback, upvote ideas, view changelogs, and see the roadmap.

## Architecture

### Technology Stack
- HTML5 (semantic layout)
- TailwindCSS via CDN
- Vanilla JavaScript (no frameworks, no builds)
- GitHub REST API v3 for backend functionality
- GitHub OAuth for authentication

### Project Structure
```
/
├── index.html             # Main entry point
├── css/
│   └── styles.css         # Custom styles beyond Tailwind
├── js/
│   ├── app.js             # Main application logic
│   ├── auth.js            # Authentication handling
│   ├── api.js             # GitHub API interactions
│   ├── ui.js              # UI components and rendering
│   ├── router.js          # Simple routing functionality
│   └── utils.js           # Helper functions
├── assets/
│   ├── icons/             # SVG icons
│   └── images/            # Images and logos
└── README.md              # Project documentation
```

## Design Language
- Inspired by ShadCN UI and Supabase's aesthetic
- Clean, minimal, premium SaaS vibes
- Primary background: White
- Secondary text and accents: Black
- Rounded corners, subtle shadows, soft color palettes
- Typography-focused, mobile-first responsive design
- Smooth hover/transition effects

## Core Features

### Authentication
- GitHub OAuth for login
- Fetch user info: username, profile picture
- Protect admin actions based on GitHub username or organization membership
- Store GitHub OAuth token securely (localStorage short-term)

### Feedback Submission
- Authenticated users can submit new feedback (Title, Description, Category)
- Creates GitHub Issues with appropriate labels

### Upvoting Functionality
- Allow users to upvote feedback via GitHub Reactions
- Show number of upvotes beside each feedback item
- Prevent multiple upvotes per user per session

### Feedback Board Display
- Pull and display all issues from the GitHub repository
- Sort and filter functionality (newest, most upvoted, most commented)
- Filter by category (Feature, Bug, Feedback)

### Changelog Section
- Fetch issues labeled as `changelog`
- Display chronologically with title, date, and author

### Roadmap Section
- Use labels for status tracking (`roadmap:planned`, `roadmap:in-progress`, `roadmap:completed`)
- Organize into columns or tabs

### Admin Controls
- Detect if user is authorized (specific GitHub username or team)
- Admin-only actions: Edit/Close issues, Post roadmap updates, Post changelog entries

## UI Components
- Navbar
- Feedback Cards
- Upvote Button
- Modal for New Submission
- Filter Bar
- Changelog View
- Roadmap View
- Loading Skeletons
- Error States

## Technical Considerations
- Handle GitHub API rate limits
- Secure GitHub OAuth flow
- Avoid exposing client secrets
- Cache data locally to reduce API calls
- Focus on performance, UX, accessibility, and maintainability