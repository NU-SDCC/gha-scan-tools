# GitHub Actions Scanning Tools

GitHub Actions a popular target for attackers right now, since GitHub Actions often has credentials, access to production, or access to release libraries.

The pipeline in this repository is meant to be usable for any project. Even if you do not have GitHub Actions, it is safe to enable this scan.

| Tool                              | Purpose                                            |
|-----------------------------------|----------------------------------------------------|
| [zizmor](https://docs.zizmor.sh/) | Better GitHub Actions linter than CodeQL provides. |

## Installation

This is available to everyone with two prerequisites:

- Any organization in the [Northwestern Secure enterprise](); and
- Repositories with GitHub Advanced Security enabled.
  - All public repositories are auto-enrolled for free by GitHub.
  - All private/internal repositories have to be enrolled either per-repo or with an organization-level policy.

An organization owner is required to set this up. This will use an organization-level repository ruleset that applies to all repositories.

1. Download the [`GitHub Actions Analysis (PR).json`](https://github.com/NU-SDCC/gha-scan-tools/blob/main/GitHub%20Actions%20Analysis%20(PR).json) template from this repo.
1. Import the template using [the instructions in the GitHub docs](https://docs.github.com/en/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization#importing-a-ruleset).
1. Pin the version by editing the newly-imported GitHub Actions Analysis (PR) ruleset -> edit the workflow configuration -> check the 'Pin to Commit' button.
1. After a few days without issues, you can change the 'Evaluate' mode to 'Enforce'.
   - The [Ruleset Insights](https://docs.github.com/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#viewing-insights-for-rulesets) page will tell you if you have errors. If there are, please contact us to investigate.

Note that this will only block PRs if the tools fail to run, *not* for their findings. You may create your own policies/rulesets for requiring findings be resolved/dismissed[^FUTURE].

[^FUTURE]: This may change in the future. As we're all getting GitHub Advanced Security set up, it creates a big backlog, so we don't want to do top-down policy for this and create problems for everyone. 

Organization owners should follow this repository for updates. When a new version is released, repeat step #3 to update to the latest version of the pipeline.

### Using the Findings

>[!NOTE]
> These checks only run on pull requests. They **do not** run on the default branch[^WHY] for direct pushes.

[^WHY]: There is no way to do a GitHub Actions required workflow for a push to the default branch using an organization-level ruleset. It's very easy to deploy this across the entire org for PRs, so that is where we're starting.

The pipeline will create GitHub Advanced Security code scanning findings. 

These will be posted in the pull request by GitHub's security bot, and the findings will be available in the 'Security and quality' tab for the repository under the branch/PR filter.