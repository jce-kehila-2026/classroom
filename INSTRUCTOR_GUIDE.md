# Instructor Guide

## Repository Structure

This repository is designed for instructors to prepare lessons and assignments for students. The repository follows a specific branching strategy to ensure that work-in-progress content is not exposed to students.

## Branch Strategy

### Main Branch
- **Purpose**: Contains finalized lessons and assignments ready for student access
- **Visibility**: Exposed to all students in the organization
- **Protection**: Only instructors can approve and merge changes to this branch
- **Guidelines**: Only merge completed, reviewed, and tested content

### Working Branches
- **Purpose**: Development and preparation of lessons and assignments
- **Visibility**: Private to instructors (not exposed to students)
- **Naming Convention**: Use descriptive names (e.g., `lesson-03-databases`, `assignment-02-api`)
- **Guidelines**: Feel free to iterate, experiment, and collaborate

## Workflow

### Preparing New Content

1. **Create a new branch** from `main`:
   ```bash
   git checkout main
   git pull origin main
   git checkout -b lesson-XX-topic-name
   ```

2. **Develop your content** on the branch:
   - Add lesson materials
   - Create assignments
   - Add tests and solutions
   - Document requirements

3. **Review and test** your content:
   - Ensure all instructions are clear
   - Test that assignments work as expected
   - Verify that solutions are correct
   - Check for any sensitive information that should not be exposed

4. **Create a Pull Request** to `main`:
   - Provide a clear description of the content
   - Request review from other instructors
   - Address any feedback

5. **Merge to main** only when:
   - Content is complete and reviewed
   - You're ready for students to access it
   - All tests pass
   - Another instructor has approved the changes

### Updating Existing Content

Follow the same process as above, but create a branch from `main` with a descriptive name like `update-lesson-XX` or `fix-assignment-YY`.

## Important Notes

- **Never commit directly to main**: Always use pull requests
- **Protect sensitive information**: Don't commit instructor notes, answer keys, or grading rubrics to main
- **Coordinate releases**: Communicate with other instructors before merging new content
- **Keep main clean**: Only merge polished, student-ready content

## Branch Protection

The repository has the following protections in place:

1. **CODEOWNERS**: The `.github/CODEOWNERS` file requires instructor approval for all changes
2. **Branch Protection Workflow**: A GitHub Action reminds reviewers that PRs to main will be exposed to students
3. **Required Reviews**: Changes to main require approval from the instructors team

## Questions?

If you have questions about the workflow or need help with repository management, contact the course administrator.
