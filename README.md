# GitHub Actions Scanning Tools

GitHub Actions a popular target for attackers right now, since GitHub Actions often has credentials, access to production, or access to release libraries.

The pipeline in this repository is meant to be usable for any project. Even if you do not have GitHub Actions, it is safe to enable this scan.

| Tool                              | Purpose                                            |
|-----------------------------------|----------------------------------------------------|
| [zizmor](https://docs.zizmor.sh/) | Better GitHub Actions linter than CodeQL provides. |

## Installation

This is available to everyone with two prerequisites:

- Any organization in the [Northwestern Secure enterprise](https://github.com/enterprises/northwestern-secure); and
- Repositories with GitHub Advanced Security enabled.
  - All public repositories are auto-enrolled for free by GitHub.
  - All private/internal repositories have to be enrolled either per-repo or with an organization-level policy.

Once those prerequisites are met, an organization administrator can opt in to this by sending a TDX ticket to `NUIT-CI-PS-CloudOps` asking them to add your organization to the 'GitHub Actions Analysis (PR)' enterprise ruleset.

No other changes are needed. When the SDCC has a new version of the pipeline, they will work with CloudOps to update it for everyone. 

### Using the Findings

>[!NOTE]
> These checks only run on pull requests. They **do not** run on the default branch[^WHY] for direct pushes.

[^WHY]: There is no way to do a GitHub Actions required workflow for a push to the default branch using an organization-level ruleset. It's very easy to deploy this across the entire org for PRs, so that is where we're starting.

The pipeline will create GitHub Advanced Security code scanning findings. 

These will be posted in the pull request by GitHub's security bot, and the findings will be available in the 'Security and quality' tab for the repository under the branch/PR filter.