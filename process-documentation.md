# Process Documentation:

## Commit Standards:

We follow the **Conventional Commits** convention. This helps in generating automated changelogs and makes the history readable.

### Types:

Use these prefixes in your commit messages to categorise the changes you are making.

| Type | Purpose | Example |
| :--- | :--- | :--- |
| **feat** | A new feature or functionality. | `feat(pdp): add product image zoom` |
| **fix** | A bug fix. | `fix(cart): resolve quantity update error` |
| **docs** | Documentation only changes. | `docs: update branching strategy guide` |
| **style** | Formatting and UI polish (no logic changes). | `style: fix button alignment on mobile` |
| **refactor** | Code changes that neither fix a bug nor add a feature. | `refactor: clean up liquid loop logic` |
| **perf** | A code change that improves performance. | `perf: lazy load collection images` |
| **test** | Adding missing tests or correcting existing ones. | `test: add checkout flow validation` |
| **build** | Changes to build tools or external dependencies. | `build: update shopify-cli version` |
| **ci** | Changes to CI configuration files and scripts. | `ci: fix github action syntax` |
| **chore** | Routine tasks (updating `.gitignore`, housekeeping). | `chore: remove unused assets folder` |
| **revert** | Undoing a previous commit. | `revert: feat: add experimental filter` |

### Format:

`<type>(<scope>): <description>`
*Example:* `feat(nav): add mobile hamburger menu`

