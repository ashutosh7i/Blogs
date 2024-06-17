---
title: "Automating Deployment with GitHub Actions and GitHub Pages 🚀🔧"
seoTitle: "Ashutosh7i"
seoDescription: "Ashutosh7i"
datePublished: Sun Jul 02 2023 13:54:39 GMT+0000 (Coordinated Universal Time)
cuid: cljlhuk3700vg9qnv16gcaovz
slug: automating-deployment-with-github-actions-and-github-pages
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688218959156/46ada98c-535a-4afd-a903-36293a4e5d6c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688219032345/aeff01be-5ead-40a7-a8ab-ac543c511e85.png
tags: github, git, githubpages, github-actions-1, gitcommands

---

In this blog post, we will explore how to automate the deployment of your web application using GitHub Actions and GitHub Pages. By setting up a GitHub Actions workflow, you can publish your application to GitHub Pages whenever you push changes to your repository. Let's get started! 💪🌐

## **What is GitHub Actions💡?**

[GitHub Actions](https://github.com/features/actions) is a powerful automation platform provided by GitHub. It allows you to define custom workflows that can be triggered based on events, such as pushing code changes, opening pull requests, or creating releases. With GitHub Actions, you can automate various tasks in your development workflow, including building, testing, and deploying your applications.

## **Setting up GitHub Pages📄**

Before we dive into setting up the GitHub Actions workflow, let's make sure you have GitHub Pages enabled for your repository. Here's how you can enable it:

1. Go to your repository on GitHub.
    
2. Click on the **Settings** tab.
    
3. Scroll down to the **GitHub Pages** section.
    
4. Select the branch you want to use for GitHub Pages (e.g., `main` or `master`).
    
5. Choose the root folder for your GitHub Pages site (e.g., `/root` or `/docs`).
    
6. Click **Save**.
    

GitHub Pages will now be enabled for your repository, and your website will be published at [`https://your-username.github.io/your-repository/`](https://your-username.github.io/your-repository/).

## **Setting up GitHub Actions Workflow⚒️**

Now that GitHub Pages is enabled, let's create a GitHub Actions workflow that automatically deploys your application whenever changes are pushed to the repository. Create a file named `.github/workflows/deploy.yml` with the following content:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main # Replace with your branch name

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Build and deploy
        uses: JamesIves/github-pages-deploy-action@3.7.1
        with:
          branch: gh-pages
          folder: ./portfolio # Replace with the folder containing your built files
```

In the above workflow, we define a job named `deploy` that runs on each push event to the specified branch (`main` by default). It uses the `actions/checkout` action to fetch the repository's code. Then, it uses the `JamesIves/github-pages-deploy-action` action to build the application and deploy it to the `gh-pages` branch.

Make sure to replace the branch name and folder path in the workflow file with your actual branch name and the folder where your built files are located.

Commit and push the workflow file to your repository, and GitHub Actions will automatically kick in whenever you push changes.

## **Creating a Simple Portfolio🧑🏻‍💻**

Now, let's create a simple portfolio webpage that we can deploy using GitHub Pages. Create an `index.html` file with the following content:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Portfolio</title>
  </head>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
    header {
      display: flex;
      align-items: center;
      padding: 20px;
    }
    header img {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      margin-right: 20px;
    }
    section {
      padding: 20px;
    }
    h1,h2 {
      color: #333;
    }
    footer {
      background-color: #f5f5f5;
      padding: 20px;
      text-align: center;
    }
    footer a {
      margin-right: 10px;
    }
  </style>
  <body>
    <header>
      <img src="https://github.com/ashutosh7i.png" alt="Profile Picture">
      <h1>Aashutosh Soni</h1>
    </header>
    <section>
      <h2>About Me</h2>
      <p>I'm a passionate web developer with experience in HTML, CSS, and JavaScript. I love creating beautiful and interactive web applications.</p>
    </section>
    <section>
      <h2>Projects</h2>
      <ul>
        <li>
          <a href="https://github.com/ashutosh7i">Project 1</a>
        </li>
      </ul>
    </section>
    <footer>
      <a href="https://github.com/ashutosh7i">GitHub</a>
      <a href="https://linkedin.com/in/ashutosh7i">LinkedIn</a>
    </footer>
  </body>
</html>
```

Update the above page, Place a profile picture in the same directory as your HTML file and replace it with `"https://github.com/ashutosh7i.png"` for your photo.

Commit and push these files to your repository.

More in out Getting started with Web Dev blog

## **Testing the Deployment🧪**

To test the deployment, make some changes to your web application code and push the changes to your repository. GitHub Actions will run the workflow, build your application, and deploy it to GitHub Pages.

Once the workflow finishes running, visit [`https://your-username.github.io/your-repository/`](https://your-username.github.io/your-repository/) to see your deployed portfolio live!

## **Conclusion✨**

By utilizing GitHub Actions and GitHub Pages, you can automate the deployment process for your web applications, making it easier to publish and share your work with the world. With this simple setup, your application will be automatically deployed to GitHub Pages whenever you push changes to your repository.

In addition to automating deployment, you can create a portfolio webpage to showcase your projects and skills. Customize the HTML and CSS code to reflect your own information and style.

Explore more possibilities with GitHub Actions and experiment with different workflows to streamline your development process. Happy coding, deploying, and showcasing your talent! 🚀💻🌐

You can check out My [Github](https://github.com/ashutosh7i) and [Linkedin](https://linkedin.com/in/ashutosh7i) (Hyperlink)😊🚀