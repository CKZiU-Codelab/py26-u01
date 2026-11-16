# py26-u01 – Card Table

**u01** · Python course 2026/27 · week 6

Each project lives in its own directory, together with the brief, my notes and
the self-check script. The brief is the source of truth; this file only
explains the workflow.

## Week 6 – Card Table

- directory: `card_table/`
- brief: `card_table/PROJEKT.md` (the same text is in `card_table/PROJEKT.pdf`)

## Workflow

1. Fork this repository to your own account (once per repository).
2. Clone your fork and add this repository as `upstream`.
3. Create a branch for the week, for example `w06-card_table`.
4. Work inside `card_table/` only.
5. Run the check before you push:

   ```bash
   cd card_table
   python3 check.py
   ```

6. Commit, push to your fork and open a pull request against `main` here.
7. Answer the review comments in the same pull request.

The first commands, once:

```bash
git clone git@github.com:<your-login>/py26-u01.git
cd py26-u01
git remote add upstream git@github.com:CKZiU-Codelab/py26-u01.git
```

## Rules

- Work only inside `card_table/`.
- Keep the files your program produced: the CSV, the images and the reports.
  They are the result, not a side effect.
- Do not edit `check.py`; it is the teacher's file.
- No secrets and no files from outside the project directory.
