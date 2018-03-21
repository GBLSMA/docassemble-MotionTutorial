# Docassemble Legal Motion Tutorial
A simple example of a Docassemble interview that automates a Word document to create a motion to dismiss.
Created by [Quinten Steenhuis](https://github.com/nonprofittechy) and [Rina Padua](https://github.com/Rinapadua).

This tutorial has been created to make use of features in Docassemble Version 0.2.39 and should work with any later version.

## How to use this tutorial
You can use this demo repository to learn the basics of creating a guided interview in Docassemble with a best-practices workflow for an individual or a small team. There are many ways to use Docassemble. When you complete this tutorial you will understand how to:

* Use a Microsoft Word document as a template for your guided interview
* Use child templates
* Make use of built-in Docassemble features for legal documents
* Use version control in Docassemble

You can use Docassemble without setting up GitHub or Google Drive. Google Drive makes the process of editing Microsoft Word templates much easier and more natural. GitHub integration [will help you](https://www.git-tower.com/learn/git/ebook/en/desktop-gui/basics/why-use-version-control) better work in a team, recover from mistakes in your code, and offer a helpful backup of your work at different points in time.

## Getting started
Follow the excellent Docassemble documentation for these first few steps:

1. [Install Docassemble](https://docassemble.org/docs/docker.html). If you just want to try out Docassemble, we recommend installing Docassemble on your laptop or workstation with [Docker](https://www.docker.com/). You may need to [enable virtualization extensions](https://www.intel.com/content/www/us/en/support/articles/000007139/server-products.html) in your computer's BIOS settings to run Docker.
1. Create a new account on [GitHub](https://www.github.com) and [Google](https://accounts.google.com/SignUp) if you don't already have accounts on both platforms.
1. Enable [GitHub](https://docassemble.org/docs/installation.html#github) and 
  [Google Drive Sync](https://docassemble.org/docs/installation.html#google%20drive) integration.
1. Create a folder in Google Drive called `docassemble-playground` (or another name of your choice).
1. Add your GitHub and Google accounts from the Profile menu in Docassemble. Connect Google Drive to the folder you created above, `docassemble-playground`.
1. [Fork](https://github.com/GBLSMA/docassemble-tutorial-motion#fork-destination-box) [this repository](https://github.com/GBLSMA/docassemble-MotionTutorial/#fork-destination-box) on GitHub.
1. [Pull](https://docassemble.org/docs/playground.html#packages) the forked repository into your playground from Folders | Packages menu. Make sure you pull the repository that you created by *forking* this repository. Forking will make a copy of the repository that you can update and change as much as you like.

![Playground Overview](https://gblsma.github.io/docassemble-MotionTutorial/images/Package-overview.png)

![Playground Overview](https://gblsma.github.io/docassemble-MotionTutorial/images/Pull-package.png)


### Configure Microsoft Word to work with Docassemble
To prevent problems, it's recommended that you [turn off automatic smart quotes](https://support.office.com/en-us/article/change-curly-quotes-to-straight-quotes-and-vice-versa-017963a0-bc5f-486b-9c9d-0ec511a8fb8f) while creating templates in Microsoft Word for Docassemble. Instructions vary. In recent versions of Word, you can turn off smart quotes by clicking File | Options | Proofing, selecting Autocorrect and uncheck the box "Smart quotes with straight quotes" under "Replace as you type" on both the Autoformat and Autoformat as you type tabs.

### A tour of the Playground
![Playground Overview](https://gblsma.github.io/docassemble-MotionTutorial/images/Playground-Overview.png)

This is a view of the Docassemble playground. You start out in the interview editing mode.

1. The Folders button lets you access different sections of the playground. You'll use this menu to switch between saving your changes to GitHub, uploading new files, and editing templates.
1. The main window that fills your screen is a text area where you can edit the interview script.
1. The list of variables can be used as a reference while you're working on the interview.

### Files included in the demo project 
This sample project includes several files to get you started:

#### Interview Files
* interview-skeleton.yml (A basic outline of an interview that assembles a Word Document. Start with this)
* interview-basic.yml (A completed version of the basic interview. Use for reference only)
* interview-withlogic.yml.yml (A completed version of the interview that uses logic. Use for reference only)

#### Template Files
* Motion to Dismiss-Original.docx (The original file that we will edit to automate it)
* Motion to Dismiss-Final.docx (A completed version of the template. Use for reference only)

## Testing the demo interview
In the Playground, select the `interview-skeleton.yml` file.

Click the "Save and Run" button to see how the interview works.
![Playground Save and Run button](https://gblsma.github.io/docassemble-MotionTutorial/images/playground-run.png)

You'll see a screen that lets you download the Word document. Notice how no questions are asked yet. That's because
we haven't added any and there are no **variables** in the template yet that need to be defined. This interview simply outputs a Word document with no customizations.

## Making your first change to a template
Let's start by opening our Word document, `Motion to Dismiss-Original.docx` in the `docassemble-playground` folder in your Google Drive account. You should *sync* this folder to your local computer for the simplest workflow.

Try making a change anywhere in the document. A classic first programming exercise is to output the text "Hello, World."
Try adding the text "Hello, World" somewhere in the document and save the file.

Wait 10-20 seconds, and click the Sync button in the playground again. Try running the interview one more time and verify that the text "Hello, World" is now in your template file.

## Making your first edit to an interview
Interviews use `YAML`

In the Playground, select the `interview-skeleton.yml` file. You should notice how the interview file contains two different sections: a "[metadata](https://docassemble.org/docs/initial.html#metadata)" section, and an [attachment](https://docassemble.org/docs/documents.html#attachment) block that begins with the line "Mandatory" that includes the filename `Motion to Dismiss-Original.docx`. It may be useful to know that each section, separated by three dashes `---`, is called a document in the `YAML` file format of a docassemble interview. Each interview page will have its section in the interview file. Indentation is important in the interview file. It tells Docassemble how to interpret the information in the interview file. Docassemble makes it easy to set the right indentation by using the `[TAB]` key.

We'll start by customizing the page where we can download our document. Let's try adding a [subquestion](https://docassemble.org/docs/questions.html#subquestion) instruction to our download screen. Review the [documentation for a subquestion instruction](https://docassemble.org/docs/questions.html#subquestion).

Let's change our download page to include the text "Hello, Download.". Try it on your own first, then read ahead. 

To do this, your interview file should now have a line directly underneath the line that begins with `Your documents are ready.` that looks like this:
```yaml
subquestion: |
  Hello, Download.
```

Notice the vertical pipe `|`. It's a best practice to include this to avoid glitches with Docassemble. Whenever you use it,
make sure to include a space after the `:` and indent the following line.

Run the interview again and confirm that the download screen now includes the text `Hello, Download.`

## Understanding code blocks
[Code](https://docassemble.org/docs/code.html) blocks allow us to add logic to an interview. You don't need to be a programmer to use `Code` blocks. There are a few key things to know though:

1. `Code` blocks use `Python` syntax. If you get stuck or run into an error, 

## Committing your first changes to Github
Let's save our work so far. It's a good practice to commit to Github whenever you make a working change to your interview or template.

Use the Folders menu to navigate to the Packages page. Look over the fields on this page. Notice that if you have multiple packages that you are working on, the package name will be a dropdown menu that you can use to select the package that you wish to update.
![Package Screen](https://gblsma.github.io/docassemble-MotionTutorial/images/Package-firstcommit.png)

Try updating the Author and Author Email to your own name. Notice that you can select files from the Playground to include the package. If you want to add additional files to the package later, here is where you will do it. Only files that you select on this screen will be committed to Github.

Scroll down to the bottom of the page and click Save, and then the Github button.

![Github button](https://gblsma.github.io/docassemble-MotionTutorial/images/github-button.png)

Set the Commit message to something descriptive, such as "Added 'Hello, World'"
![Github commit](https://gblsma.github.io/docassemble-MotionTutorial/images/Github-commit.png)


### Building the demo interview

#### Fields: Identifying the information we need to gather

#### Writing interview questions

#### Putting it all together

# Conclusion
