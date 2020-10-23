# UCL Hub Meta

This `UCLHub/meta` repository is used to track:

- Product design
- Cross-repository
- Implementation progress
- Bug identification, reproduction and fixing
- Testing
- Documentation efforts (code docs, API docs, user guides, etc.)
- CI/CD

Development of UCL Hub assumes that we eventually adopt some sort of
rolling-release model, i.e. we have a **stable** version that is ready for
production, and a **nightly** version that has the most recent developments
but may not be as stable (useful for testing and evaluation).

## Progress Tracking

To track our progress in the previously mentioned aspects, we use **milestones**
to track iterations of the project.

- For major components/features, contributors may wish to create:
	- **Organization Project Boards**: to track progress for features/bugs that
	  affect multiple repositories (such as features that affect front-ends and
	  back-end(s)).
	- **Repository Project Boards**: to track progress for features/bugs that
	  affect individual repositories (such as refactoring progress in one
	  of the front-end respoitories).

Since GitHub doesn't (yet) have native support for hierarchical issues (think
Jira-like Epics, Stories and Tasks), we utilize **labels** on issues to
and pull requests manually enforce hierarchical constraints and track
requirement analysis, design and implementation progress.

- For instance, there may be a Tracking Issue for User Accounts Subsystem;
  that subsystem itself has a Tracking Issue for User Avatars feature; that
  feature may consist of sub-features such as uploading an avatar.
- Labelled issues can be referenced in Project Boards and Milestones to track
  progress.

### Issues

Issues typically are of the following categories (possibly hierarchical):

- Requirement and Implementation.
	- We distinguish between *user-orientated requirements* versus
	  *implementation* to satisfy those requirements.
	- For *user-orientated requirements*, where a requirement may be
	  *decomposed* into smaller requirements of varrying granularity:
		- **Epic**: general use case that is a collection of features (user
		  stories).
		- **User Story**: user feature (standalone or a collection of user
		  tasks).
		- **User Task**: a small task (or sequence of steps) to satisfy the
		  user requirement.
  	- For *developer-orientated implementation* work, they are tracked by the
  	  previously enumerated requirements, in addition to **Technical Tasks**
  	  which may not necessarily be connected to a particular requirement but is
  	  necessary for develop (e.g. CI/CD infrastructure).
- Bug reports
	- Performance or correctness
- Discussions
- Feature Request
	- Different from requirements as this may be merely ideas and are not
	  properly designed/analyzed/broken-down yet.
- Missing/incorrect/invalid/confusing/needs documentation
- Infrastructure-related (CI/CD)
- Affected/involved teams
- Affected/involed subsystem (e.g. which front-end, back-end)
- Meta

### Labels

**Labels** are useful for filtering/classifying issues and pull requests and to
convey additional information about them.

Some labels may only be applicable for pull requests, while others may only be
applicable for issues. In this section, we do not explicitly dintinguish them.

It requires contributors to **triage** issues and pull requests and assign them
suitable labels.

Each label generally has the form `<A>-<identifier_separated_by_underscores>`
with `<A>` being a single-character or very short prefix, followed by a dash,
and finally followed by an identifier for the label. When the identifier needs
to consist of multiple words, it should be separated by underscores, e.g.
`<identifier_separated_by_underscores>`. If the identifier includes acronyms
such as `HTTP`, it should be lowercase, e.g. `A-http_server_diagnostics`.

#### Requirements and Implementation

Every requirement gets labelled `C-requirement`, and every
implementation-related issue gets labelled `C-implementation`.

##### Estimated Development Cost Classifications

- **Epic**: `E-epic` (longer)
- **User Story**: `E-user-story` (moderate)
- **User Task**: `E-user-task` (shorter)
- **Technical Task**: `E-technical-task` (unspecified)

Note that if necessary, **tasks** can infinitely recurse into **sub-tasks** so
as long as the ancestor tasks serve as tracking issues for child tasks.

##### Semantics

Each of these requirement/implementation may also involve the creation of
**Area** or **Features** labels.

- An **area** label is typically used for **epics**, in the form
  `A-<epic_name>`.
- A **feature** label is typically used for smaller **user story** or
  **user tasks**, in the form `F-<feature_name>`.

#### Bug Reports

Bug reports typically need to gather as much information as possible.

Every bug report gets labelled `C-bug`.

We need to have several metadata for bugs for easier classification:

- **Kind**: what kind of bug is this? (non-exhaustive, don't necessarily need
  to be labelled as these special class of bugs)
	- **Security**: `BK-security`
	- **Unsound**: `BK-unsound` (code that triggers UB or violates safety rules
	  of various languages)
	- **Privacy**: `BK-privacy`
	- **Accessibility**: `BK-accessibility`
	- **Internationalization**: `BK-internationalization`
	- **Localization**: `BK-localization`
- **Priority**: how bad is this bug? Is it bad enough to block a stable release?
	- **Won't Fix**: `P-wont_fix`
	- **Low**: `P-low`
	- **Medium**: `P-medium`
	- **High**: `P-high`
	- **Blocking/Critical**: `P-blocking`
- **Regression**: is this a new bug that occurs in `stable` or `nightly`, or
  is this a regression? If it is a regression:
  	- **Regression from one stable version to another**: `R-stable_to_stable`
  	- **Regression from stable to nightly**: `R-stable_to_nightly`
- **Reproduction**: what is the necessary environment to reproduce the bug?
	- **Operating System**: `O-<operating_system_name>`, e.g. `O-macos`
	- **Browser** (if applicable): `B-<browser_name>`, e.g. `B-firefox`,
	  `B-firefox_developer_edition`
- **Information**: is there sufficent information in the bug report?
	- **Insufficient Info**: `I-needs_more_info`
	- **Needs Minimal Complete and Verifiable Example**: `I-needs_mcve`
	- **Cannot Reproduce**: `I-cannot_reproduce`
	- **Invalid**: `I-invalid`
- **Difficulty for Contributors**: if a newcomer was interested in contributing
  a fix, what is the estimated level of difficulty?
  	- **Newcomer-friendly**: `L-newcomer_friendly`
  	- **Easy**: `L-easy`
  	- **Medium**: `L-medium`
  	- **Hard** `L-hard`

#### Discussions

Every discussion gets labelled `C-discussion`.

- **Discussion resolved**: `DI-resolved`
- **Discussion off-topic**: `DI-off_topic`

#### Feature Requests

Every feature request gets labelled `C-feature_request`.

- **Feature request accepted**: `FR-accepted`
- **Feature request closed**: `FR-closed`
- **Feature request implemented**: `FR-implemented`

#### Documentation

Every documentation issue/PR gets labelled `C-documentation`

- **Missing documentation**: `D-missing`
- **Incorrect/invalid documentation**: `D-incorrect`
- **Missing examples**: `D-missing_examples`
- **Confusing documentation**: `D-confusing`
- **Improvements to documentation**: `D-improvement`

#### Infrastructure-Related

Every infrastructure-related issue/PR gets labelled `C-infrastructure`.

- **CI/CD**: `X-deployment`
- **Bots**: `X-bots`

#### Affected Teams

- **Design**: `T-design`
- **Front-end**: `T-frontend`
- **Back-end**: `T-backend`
- **Testing and Evaluation**: `T-testing_evaluation`
- **Community**: `T-community`
- **Documentation**: `T-documentation`

#### Meta

Issues and pull requests about this document, process, repository, organization
that don't fit into other categories.

These issues and pull requests get labelled `C-meta`.
