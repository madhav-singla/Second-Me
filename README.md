# Open Source Contribution - Git Basics Demo


## Steps to Run the Project
1. **Clone the Repository**
   \`\`\`bash
   git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
   cd REPO_NAME
   \`\`\`

2. **Review the Project Structure**
   - Check the contents of the repository.
   - Open the \`contribution.txt\` and \`README.md\` files.

3. **Make Your Contributions**
   - Add your own improvements or suggestions.
   - Commit your changes following best practices.


## Contribution Guidelines
- Keep commits atomic and well-described.
- Follow naming conventions for files and branches.
- Resolve merge conflicts before final submission.

## Description
This repository demonstrates foundational Git concepts as part of an open-source contribution workflow. It covers essential practices including cloning, forking, branching, committing, creating pull requests, managing .gitignore rules, editing README documentation, and resolving merge conflicts.


## License
This project is open source and available under the [MIT License](LICENSE).

EOF

name: Welcome New Contributors


on:
  pull_request_target:
    types: [opened]

jobs:
  welcome:
    runs-on: ubuntu-latest
    if: github.event.pull_request.author_association == 'FIRST_TIMER' || github.event.pull_request.author_association == 'FIRST_TIME_CONTRIBUTOR'
    steps:
      - name: Greet the contributor
        uses: actions/github-script@v6
        with:
          script: |
            github.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: "🎉 Welcome to the project! Thank you for your first contribution. We’re happy to have you here! 🚀"
            })