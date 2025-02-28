# hugo-mock-landing-page

## Hugo GitHub Pages Workflow

This repository uses GitHub Actions to automatically build and deploy a Hugo website to GitHub Pages.

#### 🚀 Workflow Overview

Whenever changes are pushed to the `main` branch, the following process happens automatically:

1. The repository is checked out with all its submodules (including Hugo themes)
2. Hugo environment is set up with the extended version
3. The website is built using Hugo
4. The generated static files are published to the `gh-pages` branch
5. GitHub Pages serves the content from this branch

#### 🛠️ Technical Details

###### GitHub Actions Workflow

The workflow is defined in `.github/workflows/gh-pages.yml` and consists of the following steps:

- **Check Out Repository**: Clones the repository including all submodules (essential for Hugo themes)
- **Setup Hugo**: Installs Hugo v0.144.1 (extended version)
- **Build Site**: Runs `hugo -D --gc --minify` to build the site
- **Deploy**: Pushes the built site to the `gh-pages` branch

###### Build Command Flags

The Hugo build uses several important flags:

- `-D`: Includes draft content (you may want to remove this for production)
- `--gc`: Runs garbage collection to clean up cache files
- `--minify`: Reduces file sizes by removing whitespace and comments

###### Custom Domain (Optional)

If you want to use a custom domain:

1. Uncomment the `cname` line in the workflow file
2. Replace `mydomain.com` with your actual domain
3. Configure your DNS settings to point to GitHub Pages

#### 📋 Requirements

- A Hugo website repository on GitHub
- Hugo themes included as Git submodules (or directly in the repository)
- Proper repository permissions for GitHub Actions

#### 🔧 Configuration

To modify the workflow:

1. Edit the `.github/workflows/gh-pages.yml` file
2. Adjust the Hugo version if needed
3. Modify build flags to suit your needs
4. Commit and push changes to the `main` branch

#### 🚨 Troubleshooting

If the deployment fails, check:

- GitHub Actions logs for detailed error messages
- That your Hugo theme is correctly set up as a submodule
- That the Hugo version is compatible with your theme and site configuration
- That you don't exceed GitHub Pages storage limits (1GB per repository)

#### 📚 Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [peaceiris/actions-hugo](https://github.com/peaceiris/actions-hugo)
- [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages)
