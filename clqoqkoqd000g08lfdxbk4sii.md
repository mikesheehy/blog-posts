---
title: "Installing Git and Syncing with GitHub"
datePublished: Thu Dec 28 2023 05:00:10 GMT+0000 (Coordinated Universal Time)
cuid: clqoqkoqd000g08lfdxbk4sii
slug: installing-git-and-syncing-with-github
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1715892018540/0d808cf1-94a7-4571-8729-7e092448d2cf.png
tags: github, git

---

Whether collaborating on a group project or working on your own projects, [Git](https://git-scm.com/) can be a powerful tool to save and share your code. Although incorporating Git can come at any point in your coding journey, many developers recommend starting a new project with Git. Once you have Git installed, you'll be able to start showing off your projects to otherer developers and potential employers on [GitHub](https://github.com/).

To get started, you'll need to:

1. Install [Git](https://git-scm.com/) and use the default installation instructions
    
2. Create an account on [GitHub](https://github.com/)
    

Although there are several methods to start your first project using Git, creating your repository, or repo, on GitHub first may be the best option.

Benefits from starting your repo on GitHub:

1) Step-by-step walkthrough provided by GitHub

2) Fewer chances of error on both project initialization and sync to GitHub

Once you create a GitHub account, you can create your first repo by clicking on the New button at github.com.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703732715949/e1e93bd7-d373-4cf4-a7eb-439062931dae.png align="center")

Ignore repository template and name the repository. This will also be the name of the repository folder when added to your computer. You can choose to set the repository as Private, but if you want to share your project with others, you'll want to set the repository to Public.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703732944958/4ae4c0cd-5dcc-4224-a5b9-415b7d7cdbdf.png align="center")

Adding a README file can be beneficial to others viewing your project. A README file is a markdown file that will explain your project and provide instructions to users to view or edit the repo. You can add or remove a README file from your project at any time. When finished, click Create Repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703733198517/2e31c083-493f-4f4e-8849-feafcf74fc9c.png align="center")

You have now created your first repository! However, it's only in GitHub right now, and we need it synced to your computer. To do this, we'll clone the GitHub repository to your computer. Click the Code button and copy the URL provided in the HTTPS tab.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703733788843/d4824b05-b7c9-4dca-a1c9-987f8d21768d.png align="center")

Choose a folder on your computer where you want to store this repo. Typically, a developer will create a folder in their Documents folder or Desktop called "repo" or "git". In this example, I'm going to create a folder in my Documents folder called "git".

After you create your folder, open Git Bash. You will need to change directory (cd) to your new folder.

`cd Documents/git`

If you get an error, check your spelling and make sure your new folder is located where you expect. Below is what you should expect to see if you changed your directory successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703734576955/69bf3a67-0b32-4171-99d5-33d925af10de.png align="center")

Next, clone the repo using your copied URL.

`git clone` [`https://github.com/mikesheehy/MyFirstProject.git`](https://github.com/mikesheehy/MyFirstProject.git)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703735090375/24d73d45-e1d6-4c00-960c-af855357a57a.png align="center")

Now you have your repository in both GitHub and on your computer, but how do I update my project? Will I have to make changes in both places? In the next post, I'll walk through updating the new Git repo.