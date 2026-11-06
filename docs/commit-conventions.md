# Commit Conventions

We use **Conventional Commits**, written in **English**.

```
type(scope): short description
```

## Parts

| Part | Meaning | Example |
|------|---------|---------|
| `type` | Kind of change | `feat`, `fix`, `style` |
| `scope` | Part of the site (optional) | `donation`, `navbar`, `partners` |
| `description` | What you did, short | `add amount selector` |

## Types

| Type | Use it when... | Example |
|------|----------------|---------|
| `feat` | You add something new | `feat(partners): add logo grid` |
| `fix` | You correct a mistake | `fix(navbar): align logo on mobile` |
| `style` | You change looks only (spacing, colors, fonts) | `style(footer): increase padding` |
| `docs` | You change documentation | `docs(readme): explain setup steps` |
| `refactor` | You reorganize code without changing how it looks | `refactor(pages): remove repeated markup` |
| `chore` | Maintenance: config, file moves, scripts | `chore(package): add build script` |

## Writing rules

1. Type and description in lowercase.
2. Imperative mood (command form): `add`, `fix`, `remove`. Not `added` or `adds`.
3. No period at the end.
4. Maximum **72 characters**.
5. Say **what** changed, not how you feel about it.
6. One commit = one clear change.

## Good commits

```
feat(donation): add amount selector with preset values
fix(navbar): correct logo position on small screens
style(partners): reduce gap between logo cards
docs(contributing): add pull request checklist
chore(assets): rename hero image to hero-banner.jpg
refactor(about): split team section into a block
```

## Bad commits

| Bad message | Why | Better version |
|-------------|-----|----------------|
| `cambios` | Not in English, says nothing | `feat(donation): add amount selector` |
| `update` | Too vague | `fix(navbar): correct logo alignment` |
| `final final v2` | Describes a file version, not a change | `style(footer): adjust text color` |
| `fix stuff` | Which stuff? | `fix(partners): restore broken image link` |
| `Added new page.` | Past tense, period at the end | `feat(contact): add contact page` |
| `wip` | Not a finished change | Commit only when the change is complete |

## Small commits

Instead of one big commit at the end:

```bash
git commit -m "feat(donation): add page structure"
git commit -m "style(donation): style the amount buttons"
git commit -m "feat(donation): add thank you message"
```

Small commits are easier to review and to undo.