---
name: update-this-repo-and-push
description: Closing hook for finalizing and pushing this repo after skill-change commits
---

Use this as the closing hook after skill changes are already committed. Verify skill metadata consistency, ensure `README.md` skill tables reflect current skill names/descriptions, then push the current branch so committed skill updates are published.

Pay attention to the table headings, which categorize the skills. If you added a new skill, make sure to add it to the appropriate table based on its category (e.g., Economic Vibing, Student Survival, Meta Core). If you modified an existing skill, ensure that its name and description in the table are updated accordingly.
