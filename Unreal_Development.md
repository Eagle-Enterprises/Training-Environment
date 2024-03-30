# Workflow for Unreal Project Updates

In this document, we will outline the workflow for managing updates to an Unreal Engine project using version control (e.g., Git) and ensuring that each update is properly documented with a branch, story work, and a screen capture recording before merging into the main branch.
Prerequisites

    Unreal Engine installed on your machine.
    Version control system (e.g., Git) set up for your project.
    Screen capture software (e.g., OBS) installed.

## Workflow Steps

1. Create a Branch

    Before starting work on any update, create a new branch from the main branch.
    Name the branch descriptively, such as including the feature or fix being
    worked on.

    bash

    git checkout -b feature/your-feature-name

    For an example branch, see the asset-import

2. Work on the Story

    Implement the necessary changes, features, or fixes within the created branch.
    Follow your team's coding standards and best practices.
    Regularly commit your changes with descriptive commit messages.

    bash

    git add .
    git commit -m "Implemented feature XYZ"

3. Record a Screen Capture

    Before pushing your changes into the main branch, record a screen capture
    of the implemented feature or fix using screen capture software like OBS.
    Make sure the recording clearly demonstrates the functionality and any visual
    changes introduced.

4. Push into Main

    Once the changes have been reviewed, tested, and the screen capture recorded,
    push your branch into the main branch. Tag @Cybower (Adam) and @vino74611
    (Serena) as reviewers on the Push Request

5. Documentation

    Update any relevant documentation, such as README files, to reflect the changes
    introduced in the update.Include the screen capture recording in the documentation
    for future reference.

Conclusion

Following this workflow ensures that updates to the Unreal Engine project are properly managed, documented, and tested before being merged into the main branch. By creating branches for each update, working on the story within those branches, and recording screen captures, you maintain a clear history of changes and provide valuable documentation for the project's development process.
