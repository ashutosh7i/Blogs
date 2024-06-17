---
title: "Version Control with Git: A Dev's Best Friend 🌟"
seoTitle: "Ashutosh7i"
seoDescription: "Ashutosh7i"
datePublished: Sat Jul 01 2023 12:01:05 GMT+0000 (Coordinated Universal Time)
cuid: cljjycnrg000d0amifsyfhmuz
slug: version-control-with-git
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688212592673/868292d1-4c3f-4ebd-b9d0-b7f65c6afa48.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688212844200/5806b542-b8f9-455f-b1fa-980edd483ac7.png
tags: github, git, devops, gitlab, gitcommands

---

As a developer, you might have heard about Git, a powerful version control system that revolutionized the way we collaborate and manage code. In this blog post, we will explore the fundamentals of Git, including repository management, branching, merging, and collaborating with other developers. Let's dive in and master Git! 💻🚀

## What is Git?💡

Git is a distributed version control system made by [Linux Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds), The same guy who made Linux (read my [Linux](https://ashutosh7i.hashnode.dev/getting-started-with-linux) article here) designed to track changes in your codebase and facilitate collaboration among developers. It allows you to keep a complete history of your project, create branches for different features, merge changes seamlessly, and easily revert to previous versions if needed. Git's popularity stems from its speed, efficiency, and flexibility.

## Setting Up Git🧑🏻‍💻

Before we begin, ensure that you have Git installed on your system. You can download and install Git by following the instructions on the official website (link: [git-scm.com/downloads](https://git-scm.com/downloads)).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688212721841/b1aba536-19a3-4226-a874-1ec15b39796a.png align="center")

Once installed, open your terminal and configure your name and email address:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## **Git Basics**📚

### **Creating a Repository🧑🏻‍🔧**

To start using Git, you need to initialize a repository. Navigate to your project directory and run the following command:

```bash
git init
```

### **Tracking Changes**

Git tracks changes made to files within your repository. To add files for tracking, use the following command:

```bash
git add filename
```

### **Committing Changes**

Once you've added files, it's time to commit your changes. A commit is like taking a snapshot of your code at a specific point in time. Use the following command to create a commit:

```bash
git commit -m "Your commit message"
```

ProTip- keep the commit message meaningful so Other developers and you in the future grasp the code easily, There is a standard around this, it is called "Conventional commit messages", more [here](https://www.conventionalcommits.org/en/v1.0.0/)

| Commit Message | Description |
| --- | --- |
| `feat` | A new feature or functionality added to the codebase |
| `fix` | A bug fix or resolving an issue |
| `chore` | Routine tasks, maintenance, or refactoring |
| `docs` | Documentation updates or additions |
| `style` | CSS, formatting, or styling changes |
| `test` | Adding or modifying tests |
| `refactor` | Code changes that don't add new features or fix bugs |
| `perf` | Performance improvements |
| `build` | Changes related to the build system, dependencies, or CI/CD setup |
| `ci` | Changes to the continuous integration or deployment configurations |
| `revert` | Reverting a previous commit |

Example-

```bash
git commit -m "feat: Add user authentication feature"
git commit -m "fix: Resolve issue with login page not rendering properly"
```

### **Branching🌿**

Branching allows you to create independent lines of development. To create a new branch, use the following command:

```bash
git branch branch_name
```

### **Switching Branches**

To switch to a different branch, use the following command:

```bash
git checkout branch_name
```

### **Merging Branches**

Merging combines changes from one branch into another. To merge a branch, switch to the target branch and run the following command:

```bash
git merge source_branch
```

### **Collaborating with Other Developers**

Git enables seamless collaboration with other developers. You can share your code by pushing your local changes to a remote repository and pull changes made by others. Use the following commands:

```bash
git push origin branch_name
git pull origin branch_name
```

## **Best Practices and Tips✨**

To make the most out of Git, here are some best practices and tips:

1. **Commit Frequently**: Commit small, logical changes with descriptive commit messages.
    
2. **Use Meaningful Branch Names**: Choose meaningful names that reflect the purpose of the branch.
    
3. **Write Good Commit Messages**: Provide clear and concise messages that explain the changes made in the commit.
    
4. **Pull Before Push**: Always pull the latest changes from the remote repository before pushing your changes.
    
5. **Use .gitignore**: Create a .gitignore file to exclude files and directories that should not be tracked by Git (e.g., temporary files, dependencies).
    
6. **Review Pull Requests**: When collaborating with others, carefully review and test code changes before merging.
    

## **Start Mastering Git Today!🚀**

With its powerful features and versatility, Git is a developer's best friend. By mastering Git, you can effectively manage your code, collaborate seamlessly with others, and maintain a clean and organized project history.

Keep practising, exploring advanced Git workflows, and learning from the vibrant Git community. Happy coding! 🎉😄