# GitHub Repository Settings Configuration

This document provides the recommended GitHub settings to ensure that only the `main` branch is exposed to students while instructors can work on preparing content.

## Required Repository Settings

### 1. Branch Protection Rules for `main`

Navigate to: **Settings → Branches → Add branch protection rule**

Configure the following for the `main` branch:

#### Basic Settings
- **Branch name pattern**: `main`
- ✅ **Require a pull request before merging**
  - ✅ **Require approvals**: 1 (minimum)
  - ✅ **Dismiss stale pull request approvals when new commits are pushed**
  - ✅ **Require review from Code Owners**
- ✅ **Require status checks to pass before merging**
  - Search and add: `check-branch-protection` (from our workflow)
- ✅ **Require branches to be up to date before merging**
- ✅ **Require conversation resolution before merging**

#### Additional Settings
- ✅ **Do not allow bypassing the above settings** (unless you want admins to be able to bypass)
- ✅ **Restrict who can push to matching branches**
  - Add team: `@jce-kehila-2026/instructors`
- ✅ **Allow force pushes**: ❌ (disabled)
- ✅ **Allow deletions**: ❌ (disabled)

### 2. Repository Access Control

Navigate to: **Settings → Collaborators and teams**

#### Teams Configuration

1. **Create an "instructors" team** (if not already exists):
   - Organization Settings → Teams → New team
   - Team name: `instructors`
   - Add all instructor accounts to this team

2. **Create a "students" team** (if not already exists):
   - Organization Settings → Teams → New team
   - Team name: `students`
   - Add all student accounts to this team

3. **Set Repository Access**:
   - Settings → Collaborators and teams
   - Add team: `@jce-kehila-2026/instructors` with **Write** or **Maintain** access
   - Add team: `@jce-kehila-2026/students` with **Read** access

### 3. Branch Visibility

By default, students with **Read** access can see all branches. To limit their visibility to only the `main` branch, you have these options:

#### Option A: Using Separate Repositories (Recommended)
- Use this repository as the instructor workspace
- Set up an automated sync or manual releases to a separate public repository for students
- Students only access the public repository

#### Option B: GitHub Classroom (if applicable)
- Use GitHub Classroom to create individual/team repositories for students
- This repository remains private to instructors
- Assignments are distributed through GitHub Classroom

#### Option C: Branch Access Documentation
- Document clearly that students should only use the `main` branch
- Instructors use clear branch naming (e.g., `instructor/prep-lesson-03`)
- Students with read access can see branches but cannot modify them

### 4. Default Branch

Navigate to: **Settings → General → Default branch**

- Ensure `main` is set as the default branch
- This ensures students clone the correct branch by default

### 5. Repository Features

Navigate to: **Settings → General → Features**

Configure the following:
- ✅ **Issues**: Enable if you want to track tasks/bugs
- ✅ **Projects**: Enable if you want to use project boards
- ✅ **Discussions**: Enable if you want a forum (optional)
- ✅ **Wikis**: Disable (use markdown files in repo instead)

### 6. Actions Permissions

Navigate to: **Settings → Actions → General**

- **Actions permissions**: Allow all actions and reusable workflows
- **Workflow permissions**: Read and write permissions
- ✅ **Allow GitHub Actions to create and approve pull requests**: Disabled

## Verification Checklist

After applying the settings above, verify:

- [ ] The CODEOWNERS file is in place (`.github/CODEOWNERS`)
- [ ] Branch protection is active on `main` (check for shield icon in branches page)
- [ ] The `instructors` team exists and has Write/Maintain access
- [ ] The `students` team exists and has Read access
- [ ] The branch protection workflow is enabled (`.github/workflows/branch-protection.yml`)
- [ ] Instructors can create branches and open PRs
- [ ] Students can clone and read the `main` branch
- [ ] Students cannot push to any branch
- [ ] Direct pushes to `main` are blocked (even for instructors)
- [ ] PRs to `main` require instructor approval

## Testing the Setup

1. **As an instructor**:
   ```bash
   git checkout -b test-branch
   echo "test" > test.txt
   git add test.txt
   git commit -m "Test commit"
   git push origin test-branch
   # Create PR to main - should work
   ```

2. **As a student** (read-only access):
   ```bash
   git clone https://github.com/jce-kehila-2026/classroom.git
   cd classroom
   git checkout main
   # Try to push - should be denied
   ```

## Maintenance

- **Add new instructors**: Add them to the `@jce-kehila-2026/instructors` team
- **Add new students**: Add them to the `@jce-kehila-2026/students` team
- **Update protection rules**: Modify as needed based on team workflow

## Notes

- These settings ensure that only reviewed and approved content reaches the `main` branch
- Students can read but not modify the repository
- Instructors collaborate on feature branches and merge via pull requests
- The CODEOWNERS file ensures proper approval workflow
- The branch protection workflow provides helpful reminders

## Implementation Steps

To implement these settings:

1. Navigate to the repository on GitHub
2. Click "Settings" in the top navigation
3. Follow each section above to configure the settings
4. Test the configuration with instructor and student accounts
5. Document any deviations from this guide for your team

## Questions?

If you need help configuring these settings, contact the GitHub organization administrator or refer to the [GitHub documentation on branch protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).
