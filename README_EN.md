# hunter-personal-website

Personal website project built with Vue 3, TypeScript, and Tailwind CSS

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Vue](https://img.shields.io/badge/Vue-3.5-brightgreen.svg)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue.svg)
![Vite](https://img.shields.io/badge/Vite-7.x-646CFF.svg)
![Node](https://img.shields.io/badge/Node-%3E%3D20.19-339933.svg)

🌍 [简体中文](README.md) | **English**

## Features

- 📱 Responsive design for mobile and desktop
- 🎨 Modern UI design
- 🚀 Automatically fetch project information from GitHub API
- ⚡ Fast development and build with Vite
- 💻 TypeScript type safety

## Quick Start

### 1. Install Dependencies

```bash
pnpm install
```

### 2. Configure Environment Variables

Copy the `.env.example` file and rename it to `.env`:

```bash
cp .env.example .env
```

Then edit the `.env` file and fill in your GitHub username:

```env
# GitHub Configuration
VITE_GITHUB_USERNAME=your-github-username

# Featured repositories to display (comma-separated, leave empty to auto-fetch top 6 by stars)
# Supports two formats:
# 1. repo-name (uses the username configured above)
# 2. owner/repo-name (specify an organization or another user's repository)
VITE_FEATURED_REPOS=my-repo,my-org/org-repo,another-user/public-repo

# Social Media Links
VITE_GITHUB_URL=https://github.com/your-username
VITE_LINKEDIN_URL=https://linkedin.com/in/your-profile

# ICP Filing Number (optional, required only for websites in mainland China)
VITE_ICP_NUMBER=京ICP备12345678号-1

# Public Security Network Filing Number (optional, required only for websites in mainland China)
VITE_PSB_NUMBER=浙公网安备33021212345678号

# Formspree Form ID
VITE_FORMSPREE_ID=your-formspree-id
```

**Configuration Details:**

- `VITE_GITHUB_USERNAME`: Your GitHub username (required)
- `VITE_FEATURED_REPOS`: Repositories to display, supports the following formats:
  - `repo-name` - Repository under your personal account
  - `org-name/repo-name` - Repository under an organization or another user
  - Leave empty - Automatically fetch your top 6 public repositories by stars
  - Example: `my-project,my-org/team-project,friend/cool-repo`

### 3. Start Development Server

```bash
pnpm dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser

### 4. Build for Production

```bash
pnpm build
```

### 5. Preview Production Build

```bash
pnpm preview
```

## Project Structure

```
src/
├── components/              # Vue components
│   ├── NavBar.vue          # Navigation bar
│   ├── HeroSection.vue     # Hero banner
│   ├── AboutSection.vue    # About me
│   ├── ProjectsSection.vue # Projects showcase (fetched from GitHub)
│   ├── SkillsSection.vue   # Skills
│   ├── ContactSection.vue  # Contact form
│   └── FooterSection.vue   # Footer
├── router/                  # Route configuration
├── App.vue                  # Root component
└── main.ts                  # Entry file
```

## Tech Stack

- **Framework**: Vue 3 (Composition API)
- **Language**: TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **Routing**: Vue Router
- **API**: GitHub REST API

## Environment Variables

All environment variables must be prefixed with `VITE_` to be accessible in client-side code (this is Vite's security mechanism).

### Configuration Options

- **`VITE_GITHUB_USERNAME`**: Your GitHub username (required)
- **`VITE_FEATURED_REPOS`**: List of repositories to display (optional)
  - Leave empty: Automatically fetch top 6 repositories by stars
  - Specify repositories: Only display specified repositories, comma-separated
  - Supported formats:
    - `repo-name` - Repository under your personal account
    - `org-name/repo-name` - Repository under an organization
    - `username/repo-name` - Public repository from another user
  - Can mix formats, e.g.: `my-repo,my-org/team-project,friend/cool-repo`
- **`VITE_GITHUB_URL`**: Your GitHub profile link (optional, used for footer social media icons)
- **`VITE_LINKEDIN_URL`**: Your LinkedIn profile link (optional, used for footer social media icons)
- **`VITE_ICP_NUMBER`**: ICP filing number (optional, required only for websites in mainland China)
  - Example format: `京ICP备12345678号-1`
  - Will be displayed in footer with a link to the MIIT filing website
- **`VITE_PSB_NUMBER`**: Public Security Network filing number (optional, required only for websites in mainland China)
  - Example format: `浙公网安备33021212345678号`
  - Place the filing icon at `public/备案图标.png`
  - Will be displayed in the footer to the right of the ICP number, with an icon, linking to the MPS filing website
- **`VITE_FORMSPREE_ID`**: Formspree form ID (optional, used for contact form)
  - Visit [Formspree.io](https://formspree.io/) to register and create a form
  - Get your form ID (format: `xxxYYYzzz`)
  - Once configured, contact form submissions will be sent directly to your email

**Important Notes**: 
- The `.env` file is added to `.gitignore` and will not be committed to version control
- `.env.example` is a template file that will be committed to version control
- When deploying, configure the corresponding environment variables on your deployment platform

## License

This project is open source under the MIT License
