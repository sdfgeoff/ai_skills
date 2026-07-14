---
name: markdown-tickets
description: How to break down a task into tickets that can be worked on by subagents. This should be invoked whenever a task is large, has chunks that can be run in parallel, or needs to be done carefully.
---

The idea behind is to split a plan into individual tickets assigned to subagents, and the subagents work reviewed. This leaves you as the overseer of the process in charge of the architecture and quality without getting stuck in the details.

This skill requires subagents. If you need permission to use subagents, request this from the user now.

## STAGE 1: Setup

If it doesn't exist, create a tickets folder structure. The structure should be:
./tickets/todo
./tickets/in-progress
./tickets/done

## STAGE 2: Creating Tickets

Turn what you have been discussing with the user into tickets and put them inside the todo folder. The tickets should be named with a unique number, a phase/staging number (if there are ordering dependencies between tickets, any tickets in the same phase should be able to be completed in parallel), and a brief description of what work will be done inside the ticket. Eg:

`001-p2-create-fooifier.md`

Each ticket should contain enough information that the work can be completed autonomously. In general, a ticket should contain:

1. A brief explanation of how it fits into the larger project
2. A description of what needs to be done for the ticket to be considered complete
3. Goals and constraints on the work
4. Acceptance criteria: things that the reviewer should check.

If specifying future tickets requires information accumulated from previous tickets, inform the user of this, and do not create tickets with incomplete information.

## STAGE 3: User Reviews Tickets

The user reviews the ticket sequence you have created. They may ask for changes

## STAGE 4: Implementation

You will act as a supervisor. You'll spin up subagents to work on tickets and review tickets. You will not do any coding/work yourself, but are responsible for assigning work, moving tickets around, and ensuring the high level goals are met. If the tickets need to change slightly as the implementation progresses, this is fine. If not, discuss the changes with the user.

The flow should be:

1.  _Setup_
    You create a git worktree on a branch for the subagent. The branch should be named to match the ticket. The worktree should be located at `~/tmp`

2.  _Do Work_
    Create/assign a subagent to a ticket and tell it to work in the worktree you just created. Move the ticket into the `in-progress` folder. All changes must be committed.

3.  _Review_
    When the subagent has completed its work, you will create/assign another subagent to review that branch. The reviewer should review:

        - Code quality
        - If the ticket is complete
        - Flag security issues.
        - Check the worktree is clean. The review should not pass if the worktree is dirty. All files must be committed to the branch.

    The reviewer should clearly state in its review if it passes or further work is required. If the reviewer finds something suspicious or malicious, consider escalating to the user.

4.  _Merge and Cleanup_
    If the review passes:

         - Merge the branch into `master`
         - Move the ticket into the `done` folder.
         - Clean up the worktree
         - Clean up the subagent that did the work

    If it does not pass:

        - Hand the review to the original worker agent and ask them to address the points in the review. Effectively this returns to stage 2. When the worker is done, do stage 3 and 4 again as necessary.

    If there are more than a few rounds of review for a ticket, consider adjusting or splitting the ticket into multiple tickets and starting work on the new smaller tickets.

Actively wait for the agents, but don't hassle them too much. Give them 5 or 10 minutes to do their thing.

Continue running this process until there are no more tickets in the todo folder or a blocker/decision point is encountered.
