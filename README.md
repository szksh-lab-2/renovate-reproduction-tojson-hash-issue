# renovate-reproduction-tojson-hash-issue

This repository reproduces the issue of the Renovate built-in function `toJSON`.

## What's `toJSON`?

toJSON is a built-in function of Renovate.

https://github.com/renovatebot/renovate/blob/f5f32bdcb4661d03aeddf7631d024c001c7aef7b/lib/util/template/index.ts#L27

```ts
  toJSON: (input: unknown): string => JSON.stringify(input),
```

## Problem

toJSON returns an unexpected string when it's called with hash arguments.

https://handlebarsjs.com/guide/expressions.html#helpers-with-hash-arguments

```
toJSON currentValue=currentValue
```

## How To Reproduce

[renovate.json5](renovate.json5)

Call `toJSON` with hash arguments.

```
toJSON currentValue=currentValue
```

## A GitHub Issue reproducing the problem 

[#1](https://github.com/szksh-lab-2/renovate-reproduction-tojson-hash-issue/pull/1)

Please see the PR body.

## Expected Behaviour

```json
{
  "currenValue": "v4"
}
```

## Actual Behaviour

```json
{
  "name": "toJSON",
  "hash": { "currentValue": "v4.0.0" },
  "data": {
    "root": {
      "platform": "github",
      "upgrades": [
        {
          "gitAuthor": "renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>",
          "versioning": "docker",
          "separateMajorMinor": true,
          "separateMinorPatch": false,
          "branchPrefix": "renovate/",
          "semanticCommitType": "chore",
          "semanticCommitScope": "deps",
          "branchName": "renovate/actions-checkout-4.x",
          "additionalBranchPrefix": "",
          "branchTopic": "{{{depNameSanitized}}}-{{{newMajor}}}{{#if separateMinorPatch}}{{#if isPatch}}.{{{newMinor}}}{{/if}}{{/if}}{{#if separateMultipleMinor}}{{#if isMinor}}.{{{newMinor}}}{{/if}}{{/if}}.x{{#if isLockfileUpdate}}-lockfile{{/if}}",
          "commitMessage": "{{{commitMessagePrefix}}} {{{commitMessageAction}}} {{{commitMessageTopic}}} {{{commitMessageExtra}}} {{{commitMessageSuffix}}}",
          "commitBody": null,
          "commitMessagePrefix": null,
          "commitMessageAction": "Update",
          "commitMessageTopic": "{{{depName}}} action",
          "commitMessageExtra": "to {{#if isPinDigest}}{{{newDigestShort}}}{{else}}{{#if isMajor}}{{prettyNewMajor}}{{else}}{{#if isSingleVersion}}{{prettyNewVersion}}{{else}}{{#if newValue}}{{{newValue}}}{{else}}{{{newDigestShort}}}{{/if}}{{/if}}{{/if}}{{/if}}",
          "commitMessageSuffix": null,
          "prTitle": null,
          "groupSlug": null,
          "labels": [],
          "addLabels": [],
          "prBodyDefinitions": {
            "Package": "{{{depNameLinked}}}{{#if newName}}{{#unless (equals depName newName)}} → {{{newNameLinked}}}{{/unless}}{{/if}}",
            "Type": "{{{depType}}}",
            "Update": "{{{updateType}}}",
            "Current value": "{{{currentValue}}}",
            "New value": "{{{newValue}}}",
            "Change": "{{{displayFrom}}} → {{{displayTo}}}",
            "Pending": "{{{displayPending}}}",
            "References": "{{{references}}}",
            "Package file": "{{{packageFile}}}",
            "Age": "{{#if newVersion}}![age](https://developer.mend.io/api/mc/badges/age/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{newVersion}}}?slim=true){{/if}}",
            "Adoption": "{{#if newVersion}}![adoption](https://developer.mend.io/api/mc/badges/adoption/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{newVersion}}}?slim=true){{/if}}",
            "Passing": "{{#if newVersion}}![passing](https://developer.mend.io/api/mc/badges/compatibility/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{currentVersion}}}/{{{newVersion}}}?slim=true){{/if}}",
            "Confidence": "{{#if newVersion}}![confidence](https://developer.mend.io/api/mc/badges/confidence/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{currentVersion}}}/{{{newVersion}}}?slim=true){{/if}}"
          },
          "prBodyColumns": ["Package", "Type", "Update", "Change", "Pending"],
          "prBodyNotes": [],
          "repository": "szksh-lab-2/renovate-reproduction-tojson-hash-issue",
          "parentOrg": "szksh-lab-2",
          "topLevelOrg": "szksh-lab-2",
          "baseBranch": "main",
          "manager": "github-actions",
          "categories": ["ci"],
          "packageFile": ".github/workflows/test.yaml",
          "parentDir": "workflows",
          "packageFileDir": ".github/workflows",
          "depName": "actions/checkout",
          "datasource": "github-tags",
          "depType": "action",
          "currentValue": "v4.0.0",
          "packageName": "actions/checkout",
          "sourceUrl": "https://github.com/actions/checkout",
          "currentVersion": "v4.0.0",
          "currentVersionTimestamp": "2023-10-17T15:38:19.000Z",
          "currentVersionAgeInDays": 847,
          "isSingleVersion": true,
          "newVersion": "v4.3.1",
          "newValue": "v4.3.1",
          "releaseTimestamp": "2025-11-13T23:20:02.000Z",
          "newVersionAgeInDays": 89,
          "newMajor": 4,
          "newMinor": 3,
          "newPatch": 1,
          "updateType": "minor",
          "isMinor": true,
          "depNameSanitized": "actions-checkout",
          "sourceRepoSlug": "actions-checkout",
          "sourceRepo": "actions/checkout",
          "sourceRepoOrg": "actions",
          "sourceRepoName": "checkout",
          "recreateClosed": false,
          "displayFrom": "v4.0.0",
          "displayTo": "v4.3.1",
          "prettyNewVersion": "v4.3.1",
          "prettyNewMajor": "v4",
          "depTypes": ["action"],
          "displayPending": "",
          "prettyDepType": "action",
          "isRange": false,
          "logJSON": {
            "project": {
              "repository": "actions/checkout",
              "sourceUrl": "https://github.com/actions/checkout",
              "packageName": "actions/checkout",
              "depName": "actions/checkout"
            },
            "versions": [
              {
                "version": "v4.3.1",
                "releaseNotes": {
                  "url": "https://github.com/actions/checkout/releases/tag/v4.3.1",
                  "body": "##### What's Changed\n\n- Port v6 cleanup to v4 by @ericsciple in #2305\n\nFull Changelog: actions/checkout@v4...v4.3.1\n"
                }
              },
              {
                "version": "v4.3.0",
                "releaseNotes": {
                  "url": "https://github.com/actions/checkout/releases/tag/v4.3.0",
                  "body": "##### What's Changed\n\n- docs: update README.md by @motss in #1971\n- Add internal repos for checking out multiple repositories by @mouismail in #1977\n- Documentation update - add recommended permissions to Readme by @benwells in #2043\n- Adjust positioning of user email note and permissions heading by @joshmgross in #2044\n- Update README.md by @nebuk89 in #2194\n- Update CODEOWNERS for actions by @TingluoHuang in #2224\n- Update package dependencies by @salmanmkc in #2236\n- Prepare release v4.3.0 by @salmanmkc in #2237\n\n##### New Contributors\n\n- @motss made their first contribution in #1971\n- @mouismail made their first contribution in #1977\n- @benwells made their first contribution in #2043\n- @nebuk89 made their first contribution in #2194\n- @salmanmkc made their first contribution in #2236\n\nFull Changelog: actions/checkout@v4...v4.3.0\n"
                }
              },
              {
                "version": "v4.2.2",
                "releaseNotes": {
                  "body": "- url-helper.ts now leverages well-known environment variables by @jww3 in #1941\n- Expand unit test coverage for isGhes by @jww3 in #1946\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v422"
                }
              },
              {
                "version": "v4.2.1",
                "releaseNotes": {
                  "body": "- Check out other refs/\* by commit if provided, fall back to ref by @orhantoy in #1924\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v421"
                }
              },
              {
                "version": "v4.2.0",
                "releaseNotes": {
                  "body": "- Add Ref and Commit outputs by @lucacome in #1180\n- Dependency updates by @dependabot- #1777, #1872\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v420"
                }
              },
              {
                "version": "v4.1.7",
                "releaseNotes": {
                  "body": "- Bump the minor-npm-dependencies group across 1 directory with 4 updates by @dependabot in #1739\n- Bump actions/checkout from 3 to 4 by @dependabot in #1697\n- Check out other refs/\* by commit by @orhantoy in #1774\n- Pin actions/checkout's own workflows to a known, good, stable version. by @jww3 in #1776\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v417"
                }
              },
              {
                "version": "v4.1.6",
                "releaseNotes": {
                  "body": "- Check platform to set archive extension appropriately by @cory-miller in #1732\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v416"
                }
              },
              {
                "version": "v4.1.5",
                "releaseNotes": {
                  "body": "- Update NPM dependencies by @cory-miller in #1703\n- Bump github/codeql-action from 2 to 3 by @dependabot in #1694\n- Bump actions/setup-node from 1 to 4 by @dependabot in #1696\n- Bump actions/upload-artifact from 2 to 4 by @dependabot in #1695\n- README: Suggest user.email to be 41898282+github-actions[bot]@users.noreply.github.com by @cory-miller in #1707\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v415"
                }
              },
              {
                "version": "v4.1.4",
                "releaseNotes": {
                  "body": "- Disable extensions.worktreeConfig when disabling sparse-checkout by @jww3 in #1692\n- Add dependabot config by @cory-miller in #1688\n- Bump the minor-actions-dependencies group with 2 updates by @dependabot in #1693\n- Bump word-wrap from 1.2.3 to 1.2.5 by @dependabot in #1643\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v414"
                }
              },
              {
                "version": "v4.1.3",
                "releaseNotes": {
                  "body": "- Check git version before attempting to disable sparse-checkout by @jww3 in #1656\n- Add SSH user parameter by @cory-miller in #1685\n- Update actions/checkout version in update-main-version.yml by @jww3 in #1650\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v413"
                }
              },
              {
                "version": "v4.1.2",
                "releaseNotes": {
                  "body": "- Fix: Disable sparse checkout whenever sparse-checkout option is not present @dscho in #1598\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v412"
                }
              },
              {
                "version": "v4.1.1",
                "releaseNotes": {
                  "body": "- Correct link to GitHub Docs by @peterbe in #1511\n- Link to release page from what's new section by @cory-miller in #1514\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v411"
                }
              },
              {
                "version": "v4.1.0",
                "releaseNotes": {
                  "body": "- Add support for partial checkout filters\n",
                  "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v410"
                }
              }
            ],
            "hasReleaseNotes": true
          },
          "hasReleaseNotes": true,
          "releases": [
            {
              "version": "v4.3.1",
              "releaseNotes": {
                "url": "https://github.com/actions/checkout/releases/tag/v4.3.1",
                "body": "##### What's Changed\n\n- Port v6 cleanup to v4 by @ericsciple in #2305\n\nFull Changelog: actions/checkout@v4...v4.3.1\n"
              }
            },
            {
              "version": "v4.3.0",
              "releaseNotes": {
                "url": "https://github.com/actions/checkout/releases/tag/v4.3.0",
                "body": "##### What's Changed\n\n- docs: update README.md by @motss in #1971\n- Add internal repos for checking out multiple repositories by @mouismail in #1977\n- Documentation update - add recommended permissions to Readme by @benwells in #2043\n- Adjust positioning of user email note and permissions heading by @joshmgross in #2044\n- Update README.md by @nebuk89 in #2194\n- Update CODEOWNERS for actions by @TingluoHuang in #2224\n- Update package dependencies by @salmanmkc in #2236\n- Prepare release v4.3.0 by @salmanmkc in #2237\n\n##### New Contributors\n\n- @motss made their first contribution in #1971\n- @mouismail made their first contribution in #1977\n- @benwells made their first contribution in #2043\n- @nebuk89 made their first contribution in #2194\n- @salmanmkc made their first contribution in #2236\n\nFull Changelog: actions/checkout@v4...v4.3.0\n"
              }
            },
            {
              "version": "v4.2.2",
              "releaseNotes": {
                "body": "- url-helper.ts now leverages well-known environment variables by @jww3 in #1941\n- Expand unit test coverage for isGhes by @jww3 in #1946\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v422"
              }
            },
            {
              "version": "v4.2.1",
              "releaseNotes": {
                "body": "- Check out other refs/\* by commit if provided, fall back to ref by @orhantoy in #1924\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v421"
              }
            },
            {
              "version": "v4.2.0",
              "releaseNotes": {
                "body": "- Add Ref and Commit outputs by @lucacome in #1180\n- Dependency updates by @dependabot- #1777, #1872\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v420"
              }
            },
            {
              "version": "v4.1.7",
              "releaseNotes": {
                "body": "- Bump the minor-npm-dependencies group across 1 directory with 4 updates by @dependabot in #1739\n- Bump actions/checkout from 3 to 4 by @dependabot in #1697\n- Check out other refs/\* by commit by @orhantoy in #1774\n- Pin actions/checkout's own workflows to a known, good, stable version. by @jww3 in #1776\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v417"
              }
            },
            {
              "version": "v4.1.6",
              "releaseNotes": {
                "body": "- Check platform to set archive extension appropriately by @cory-miller in #1732\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v416"
              }
            },
            {
              "version": "v4.1.5",
              "releaseNotes": {
                "body": "- Update NPM dependencies by @cory-miller in #1703\n- Bump github/codeql-action from 2 to 3 by @dependabot in #1694\n- Bump actions/setup-node from 1 to 4 by @dependabot in #1696\n- Bump actions/upload-artifact from 2 to 4 by @dependabot in #1695\n- README: Suggest user.email to be 41898282+github-actions[bot]@users.noreply.github.com by @cory-miller in #1707\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v415"
              }
            },
            {
              "version": "v4.1.4",
              "releaseNotes": {
                "body": "- Disable extensions.worktreeConfig when disabling sparse-checkout by @jww3 in #1692\n- Add dependabot config by @cory-miller in #1688\n- Bump the minor-actions-dependencies group with 2 updates by @dependabot in #1693\n- Bump word-wrap from 1.2.3 to 1.2.5 by @dependabot in #1643\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v414"
              }
            },
            {
              "version": "v4.1.3",
              "releaseNotes": {
                "body": "- Check git version before attempting to disable sparse-checkout by @jww3 in #1656\n- Add SSH user parameter by @cory-miller in #1685\n- Update actions/checkout version in update-main-version.yml by @jww3 in #1650\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v413"
              }
            },
            {
              "version": "v4.1.2",
              "releaseNotes": {
                "body": "- Fix: Disable sparse checkout whenever sparse-checkout option is not present @dscho in #1598\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v412"
              }
            },
            {
              "version": "v4.1.1",
              "releaseNotes": {
                "body": "- Correct link to GitHub Docs by @peterbe in #1511\n- Link to release page from what's new section by @cory-miller in #1514\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v411"
              }
            },
            {
              "version": "v4.1.0",
              "releaseNotes": {
                "body": "- Add support for partial checkout filters\n",
                "url": "https://github.com/actions/checkout/blob/HEAD/CHANGELOG.md#v410"
              }
            }
          ],
          "depNameLinked": "actions/checkout",
          "newNameLinked": "undefined",
          "references": "source"
        }
      ],
      "depTypes": ["action"],
      "gitAuthor": "renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>",
      "versioning": "docker",
      "separateMajorMinor": true,
      "separateMinorPatch": false,
      "branchPrefix": "renovate/",
      "semanticCommitType": "chore",
      "semanticCommitScope": "deps",
      "branchName": "renovate/actions-checkout-4.x",
      "additionalBranchPrefix": "",
      "branchTopic": "{{{depNameSanitized}}}-{{{newMajor}}}{{#if separateMinorPatch}}{{#if isPatch}}.{{{newMinor}}}{{/if}}{{/if}}{{#if separateMultipleMinor}}{{#if isMinor}}.{{{newMinor}}}{{/if}}{{/if}}.x{{#if isLockfileUpdate}}-lockfile{{/if}}",
      "commitMessage": "Update actions/checkout action to v4.3.1",
      "commitBody": null,
      "commitMessagePrefix": null,
      "commitMessageAction": "Update",
      "commitMessageTopic": "{{{depName}}} action",
      "commitMessageExtra": "to {{#if isPinDigest}}{{{newDigestShort}}}{{else}}{{#if isMajor}}{{prettyNewMajor}}{{else}}{{#if isSingleVersion}}{{prettyNewVersion}}{{else}}{{#if newValue}}{{{newValue}}}{{else}}{{{newDigestShort}}}{{/if}}{{/if}}{{/if}}{{/if}}",
      "commitMessageSuffix": null,
      "prTitle": "Update actions/checkout action to v4.3.1",
      "groupSlug": null,
      "labels": [],
      "addLabels": [],
      "prBodyDefinitions": {
        "Package": "{{{depNameLinked}}}{{#if newName}}{{#unless (equals depName newName)}} → {{{newNameLinked}}}{{/unless}}{{/if}}",
        "Type": "{{{depType}}}",
        "Update": "{{{updateType}}}",
        "Current value": "{{{currentValue}}}",
        "New value": "{{{newValue}}}",
        "Change": "{{{displayFrom}}} → {{{displayTo}}}",
        "Pending": "{{{displayPending}}}",
        "References": "{{{references}}}",
        "Package file": "{{{packageFile}}}",
        "Age": "{{#if newVersion}}![age](https://developer.mend.io/api/mc/badges/age/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{newVersion}}}?slim=true){{/if}}",
        "Adoption": "{{#if newVersion}}![adoption](https://developer.mend.io/api/mc/badges/adoption/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{newVersion}}}?slim=true){{/if}}",
        "Passing": "{{#if newVersion}}![passing](https://developer.mend.io/api/mc/badges/compatibility/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{currentVersion}}}/{{{newVersion}}}?slim=true){{/if}}",
        "Confidence": "{{#if newVersion}}![confidence](https://developer.mend.io/api/mc/badges/confidence/{{datasource}}/{{replace '/' '%2f' packageName}}/{{{currentVersion}}}/{{{newVersion}}}?slim=true){{/if}}"
      },
      "prBodyColumns": ["Package", "Type", "Update", "Change", "Pending"],
      "prBodyNotes": [],
      "repository": "szksh-lab-2/renovate-reproduction-tojson-hash-issue",
      "parentOrg": "szksh-lab-2",
      "topLevelOrg": "szksh-lab-2",
      "baseBranch": "main",
      "manager": "github-actions",
      "categories": ["ci"],
      "packageFile": ".github/workflows/test.yaml",
      "parentDir": "workflows",
      "packageFileDir": ".github/workflows",
      "depName": "actions/checkout",
      "datasource": "github-tags",
      "depType": "action",
      "currentValue": "v4.0.0",
      "packageName": "actions/checkout",
      "sourceUrl": "https://github.com/actions/checkout",
      "currentVersion": "v4.0.0",
      "currentVersionTimestamp": "2023-10-17T15:38:19.000Z",
      "currentVersionAgeInDays": 847,
      "isSingleVersion": true,
      "newVersion": "v4.3.1",
      "newValue": "v4.3.1",
      "releaseTimestamp": "2025-11-13T23:20:02.000Z",
      "newVersionAgeInDays": 89,
      "newMajor": 4,
      "newMinor": 3,
      "newPatch": 1,
      "updateType": "minor",
      "isMinor": true,
      "depNameSanitized": "actions-checkout",
      "sourceRepoSlug": "actions-checkout",
      "sourceRepo": "actions/checkout",
      "sourceRepoOrg": "actions",
      "sourceRepoName": "checkout",
      "recreateClosed": false,
      "displayFrom": "v4.0.0",
      "displayTo": "v4.3.1",
      "prettyNewVersion": "v4.3.1",
      "prettyNewMajor": "v4",
      "displayPending": "",
      "prettyDepType": "action",
      "isRange": false,
      "hasReleaseNotes": true,
      "env": {
        "HOME": "/home/ubuntu",
        "PATH": "/home/ubuntu/.local/bin:/home/ubuntu/bin:/home/ubuntu/.local/bin:/home/ubuntu/bin:/home/ubuntu/.local/bin:/home/ubuntu/bin:/home/ubuntu/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
        "LC_ALL": "C.UTF-8",
        "LANG": "C.UTF-8"
      }
    }
  },
  "loc": {
    "start": { "line": 1, "column": 0 },
    "end": { "line": 1, "column": 40 }
  }
}
```
