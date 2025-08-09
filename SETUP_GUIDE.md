# Self-Hosting Guide for Modified GitHub Readme Stats

This guide will help you set up your own instance of GitHub Readme Stats with the following modifications:

1. **Private commits support** - Shows your private repository commits
2. **Easier A+ rating** - Modified ranking algorithm for better ratings
3. **Self-hosted** - Complete control over your data

## Prerequisites

- A GitHub account
- A Vercel account (free tier works)
- A GitHub Personal Access Token (PAT)

## Step 1: Fork the Repository

1. Go to [this repository](https://github.com/your-username/github-readme-stats) (replace with your fork URL)
2. Click the "Fork" button in the top right
3. Wait for the fork to complete

## Step 2: Create a GitHub Personal Access Token

1. Go to [GitHub Settings > Developer settings > Personal access tokens](https://github.com/settings/tokens)
2. Click "Generate new token (classic)"
3. Give it a name like "GitHub Readme Stats"
4. Select the following scopes:
   - `repo` (Full control of private repositories)
   - `user` (Update ALL user data)
5. Click "Generate token"
6. **Copy the token** - you won't be able to see it again!

## Step 3: Deploy to Vercel

### Option A: Deploy Button (Recommended)

1. Click this button: [![Deploy to Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/your-username/github-readme-stats)
2. Sign in with GitHub if prompted
3. Select your forked repository
4. Click "Import"

### Option B: Manual Deployment

1. Go to [vercel.com](https://vercel.com)
2. Sign in with GitHub
3. Click "New Project"
4. Import your forked repository
5. Click "Import"

## Step 4: Configure Environment Variables

1. In your Vercel dashboard, go to your project
2. Click on "Settings" tab
3. Click on "Environment Variables"
4. Add the following environment variable:
   - **Name**: `PAT_1`
   - **Value**: Your GitHub Personal Access Token (from Step 2)
   - **Environment**: Production (and Preview if you want)
5. Click "Save"

## Step 5: Deploy

1. Click "Deploy" in Vercel
2. Wait for the deployment to complete
3. Note your deployment URL (e.g., `https://your-project.vercel.app`)

## Step 6: Test Your Setup

### Test Private Commits

Use this URL to test if private commits are working:

```
https://your-project.vercel.app/api?username=YOUR_USERNAME&count_private=true
```

Replace:
- `your-project.vercel.app` with your actual Vercel domain
- `YOUR_USERNAME` with your GitHub username

### Test A+ Rating

The ranking algorithm has been modified to make it easier to achieve an A+ rating. The thresholds have been reduced:

- **Commits**: 500 (was 1000) for all commits, 125 (was 250) for public only
- **PRs**: 25 (was 50)
- **Issues**: 12 (was 25)
- **Reviews**: 1 (was 2)
- **Stars**: 25 (was 50)
- **Followers**: 5 (was 10)

## Usage Examples

### Basic Stats Card (Public Only)
```markdown
![Your GitHub stats](https://your-project.vercel.app/api?username=YOUR_USERNAME)
```

### Stats Card with Private Commits
```markdown
![Your GitHub stats](https://your-project.vercel.app/api?username=YOUR_USERNAME&count_private=true)
```

### Stats Card with Icons
```markdown
![Your GitHub stats](https://your-project.vercel.app/api?username=YOUR_USERNAME&count_private=true&show_icons=true)
```

### Custom Theme
```markdown
![Your GitHub stats](https://your-project.vercel.app/api?username=YOUR_USERNAME&count_private=true&show_icons=true&theme=radical)
```

## Available Parameters

- `username` - Your GitHub username (required)
- `count_private` - Include private commits (boolean, default: false)
- `show_icons` - Show icons next to stats (boolean, default: false)
- `theme` - Theme name (string, default: default)
- `hide` - Hide specific stats (comma-separated: stars,commits,prs,issues,contribs)
- `hide_rank` - Hide the rank badge (boolean, default: false)
- `card_width` - Card width in pixels (number, default: 287)

## Troubleshooting

### Private Commits Not Showing

1. Make sure your PAT has the `repo` scope
2. Verify the `PAT_1` environment variable is set in Vercel
3. Check that you're using `count_private=true` in the URL
4. Ensure your private repositories have commits

### Rate Limiting

If you hit rate limits:
1. The free tier has generous limits
2. Consider upgrading to Vercel Pro for higher limits
3. Check your GitHub token permissions

### Deployment Issues

1. Check Vercel deployment logs
2. Ensure all environment variables are set
3. Verify the repository is properly forked

## Security Notes

- Keep your GitHub PAT secure
- Don't commit the token to your repository
- Use environment variables in Vercel
- Consider using a dedicated GitHub account for the PAT

## Updates

To keep your fork updated with the original repository:

1. Go to your forked repository on GitHub
2. Click "Sync fork" button
3. Click "Update branch"
4. Redeploy on Vercel if needed

## Support

If you encounter issues:

1. Check the [original repository issues](https://github.com/anuraghazra/github-readme-stats/issues)
2. Verify your setup matches this guide
3. Check Vercel deployment logs
4. Ensure your GitHub token has the correct permissions

## License

This modified version follows the same MIT license as the original project.
