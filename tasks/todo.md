# CLI Install Skill — Todo

> Source plan: [`tasks/plan.md`](plan.md) · Source idea: [`docs/ideas/cli-install-skill.md`](../docs/ideas/cli-install-skill.md)

## Phase 1: Ship the install skill

### Task 1 — Write `skills/install/SKILL.md`
- [ ] Create `skills/install/` directory
- [ ] Write `SKILL.md` with frontmatter: `name: install`, `description: <one sentence>`, `user-invocable: true`
- [ ] Body: "When to use" section with 3 trigger conditions
- [ ] Body: canonical bash block `curl -fsSL https://specscore.md/get-cli | sh`
- [ ] Body: exit-code handling (0 → success; non-zero → surface stderr, stop)
- [ ] Body: idempotency note (re-running is safe)
- [ ] No `references/` subdirectory

---

### Checkpoint A — end-to-end install works
- [ ] `which specscore` on a clean machine returns empty
- [ ] Local plugin install succeeds
- [ ] `/specscore-cli:install` appears in slash menu
- [ ] Bash permission prompt renders the exact `curl ... | sh` command
- [ ] After approval, `which specscore` resolves
- [ ] `specscore --version` returns a semver
- [ ] **Do not proceed to Phase 2 if any of the above fails**

---

## Phase 2: Document the conventions

### Task 2 — Update `skills/README.md`
- [ ] Add `install` row to the planned skill catalogue (category: Infrastructure)
- [ ] Add "Skill categories" subsection (Infrastructure vs CLI-wrapper, ≤ 5 sentences)
- [ ] Add "Pre-flight pattern" subsection with canonical copy-paste snippet
- [ ] Snippet mentions both paths in the error (invoke `/specscore-cli:install` + manual curl)
- [ ] Update "Status: Scaffold only" note to reflect install is shipped
- [ ] All relative links resolve

---

## Phase 3: Surface it to humans

### Task 3 — Update root `README.md`
- [ ] Add "First use" section after the existing "Install" section, before "Relationship to the CLI"
- [ ] Name both paths (slash invocation + manual curl)
- [ ] ≤ 6 lines of prose
- [ ] No edits to other sections

---

### Checkpoint B — ready for review
- [ ] `skills/README.md` + `README.md` render cleanly on GitHub (push to a branch)
- [ ] All relative links resolve
- [ ] First-time-reader walkthrough: `/plugin install` → README → `/specscore-cli:install` → working CLI, with no dead ends
- [ ] Human review + approval before commit/PR
