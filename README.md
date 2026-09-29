# GitHub Actions Scanning Tools

GitHub Actions a popular target for attackers right now, since GitHub Actions often has credentials, access to production, or access to release libraries.

The pipeline in this repository is meant to be usable for any project. Even if you do not have GitHub Actions, it is safe to enable this scan.

| Tool                              | Purpose                                            |
|-----------------------------------|----------------------------------------------------|
| [zizmor](https://docs.zizmor.sh/) | Better GitHub Actions linter than CodeQL provides. |

## Usage

This is available to everyone with two prerequisites:

- Any organization in the [Northwestern Secure enterprise](); and
- Repositories with GitHub Advanced Security enabled.
  - All public repositories are auto-enrolled for free by GitHub.
  - All private/internal repositories have to be enrolled either per-repo or with an organization-level policy.

The easiest way to enable this is with an organization-level repository ruleset. 

You can import the ruleset templates using [the instructions in the GitHub docs](https://docs.github.com/en/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization#importing-a-ruleset). 

The rulesets are available here. They default to evaluate mode:

- [`org-rulesets/GitHub Actions Analysis (PR).json`](#)
