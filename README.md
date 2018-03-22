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

## A note about the technologies used in Docassemble
Docassemble makes use of many different component parts. Usually the Docassemble [documentation](https://docassemble.org/docs.html) contains everything you need to know about those components. Sometimes you run into a gap in the documentation and may decide to do your own research. Here are some of the technologies that we use in our demonstration:

* YAML for the interview file format.
* Python for logic in the interview and template.
* Mako for formatting questions in the interview file.
* Jinja2 for formatting answers in your template.

This tutorial includes everything you need to know about those technologies to complete the tutorial. However, it can helpful to know what terms to Google if you run into a stumbling block. The [Docassemble Slack channel](https://join.slack.com/t/docassemble/shared_invite/enQtMjQ0Njc1NDk0NjU2LTAzYzY5NWExMzUxNTNhNjUyZjRkMDg0NGE2Yjc2YjI0OGNlMTcwNjhjYzRhMjljZWU0MTI2N2U0MTFlM2ZjNzg) is also an excellent place to get troubleshooting assistance when a question is not answered in the [documentation](https://docassemble.org/docs.html).

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

![Pull a package](https://gblsma.github.io/docassemble-MotionTutorial/images/Pull-package.png)

## Basic concepts of document assembly
![Overview of Document Assembly](https://gblsma.github.io/docassemble-MotionTutorial/images/interview_workflow.png)

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
Interviews use `YAML` syntax. If you run into a problem with your interview file, it may help to know that you can Google YAML concepts.

In the Playground, select the `interview-skeleton.yml` file. You should notice how the interview file contains two different sections: a "[metadata](https://docassemble.org/docs/initial.html#metadata)" section, and an [attachment](https://docassemble.org/docs/documents.html#attachment) block that begins with the line "Mandatory" that includes the filename `Motion to Dismiss-Original.docx`. It may be useful to know that each section, separated by three dashes `---`, is called a document in the `YAML` file format of a docassemble interview. Each interview page will have its section in the interview file. Indentation is important in the interview file. It tells Docassemble how to interpret the information in the interview file. Docassemble makes it easy to set the right indentation by using the `[TAB]` key.

We'll start by customizing the page where we can download our document. Let's try adding a [subquestion](https://docassemble.org/docs/questions.html#subquestion) instruction to our download screen. Review the [documentation for a subquestion instruction](https://docassemble.org/docs/questions.html#subquestion).

Let's change our download page to include the text "Hello, Download.". Try it on your own first, then read ahead. 

To do this, your interview file should now have a line directly underneath the line that begins with `Your documents are ready.` that looks like this:
```yaml
subquestion: |
  Hello, Download.
```

Notice the vertical pipe `|`. It's a best practice to include this when you type in text to avoid glitches with Docassemble. Whenever you use it, make sure to include a space after the `:` and indent the following line. Two spaces is the traditional indent in Docassemble, and hitting the [TAB] key is a quick way to enter those two spaces.

Run the interview again and confirm that the download screen now includes the text `Hello, Download.`

## Understanding code blocks
[Code](https://docassemble.org/docs/code.html) blocks allow us to add logic to an interview. You don't need to be a programmer to use `Code` blocks. `Code` blocks use `Python` syntax. If you get stuck or run into an error, Googling `Python` concepts will help you solve your problem.

Let's create a very basic code block using the [example](https://docassemble.org/docs/code.html#simpleexamples) from the Docassemble documentation. This will also be our first introduction to variables. `Variable` will be used as a synonym for `field` in this tutorial.

Add a new section into your `interview-skeleton.yml` file. Don't forget to begin it with `---` on its own line. Let's assign the value 2 + 2 to a new variable named `answer`. Your completed code block should look like this:

```yaml
---
code: |
  answer = 2 + 2
```

Now lets edit our `attachment` block subquestion to state "The answer is (the value of the answer variable)". Refer back to the [example](https://docassemble.org/docs/code.html#simpleexamples) to understand how to display a variable in a question. This is our first introduction to displaying a variable in an interview. The main thing to know is that variables can be used in a question by surrounding them by `${variable_name}`. Try it on your own first. When you are finished, your attachment block should look like this:

```yaml
question: |
  Your documents are ready. Please print and file!
subquestion: |
  Hello, Download. The answer is ${answer}.
```

Finally, lets edit our locally saved template `Motion to Dismiss-Original.docx` to include the `answer` variable as well. Try it on your own first by referring to the [Filling DOCX Templates](https://docassemble.org/docs/documents.html#docx template file) documentation. When you are finished, your template should include text that looks like this:

```
Hello, World. The Answer is {% raw %}{{ answer }}{% endraw %}
```

Notice that while in an interview question, we display a variable like this: `${variable_name}` but in our template, we include a variable by surrounding it with double brackets like this: {% raw %}{{variable_name}}{% endraw %}.

Click the `GD` button to sync the playground with Google Drive and update the copy of the Word file in our Docassemble playground.

Run the interview one more time to verify your changes were made.

## Committing your first changes to Github
Let's save our work so far. It's a good practice to commit to Github whenever you make a working change to your interview or template.

Use the Folders menu to navigate to the Packages page. Look over the fields on this page. Notice that if you have multiple packages that you are working on, the package name will be a dropdown menu that you can use to select the package that you wish to update.
![Package Screen](https://gblsma.github.io/docassemble-MotionTutorial/images/Package-firstcommit.png)

Try updating the Author and Author Email to your own name. Notice that you can select files from the Playground to include the package. If you want to add additional files to the package later, here is where you will do it. Only files that you select on this screen will be committed to Github.

Scroll down to the bottom of the page and click Save, and then the Github button.

![Github button](https://gblsma.github.io/docassemble-MotionTutorial/images/github-button.png)

Set the Commit message to something descriptive, such as "Added 'Hello, World'"
![Github commit](https://gblsma.github.io/docassemble-MotionTutorial/images/Github-commit.png)

## Building the demo interview
So far we've told you exactly what to include in the interview and template. For this stage of the tutorial, you will need to do some thinking on your own. Building a guided interview has 3 basic steps:

1. Deciding what information we need to gather and coming up with descriptive `variable` names for each item of information.
1. Creating interview screens to gather the information.
1. Include the answers you gathered in the interview with formatting in your template.

### Fields: Identifying the information we need to gather
Look at the sample template `Motion to Dismiss-Original.docx`. Think about the information we need to gather in the following categories:
1. Parties
1. Locations
1. Dates
1. Conclusions and facts needed to reach those conclusions.

Try it on your own first. Mark any information in the template that will need to change (you can print and highlight on a piece of paper or write it in a separate document such as a spreadsheet).
We will need to know:
* The county
* The name of the court
* The Landlord's name
* The Tenant's name
* The Tenant's address and phone number
* Every reason for dismissing the case, numbered 1-3 in the example document.
* The date of service
* The type of service

Write down logical variable names for each piece of information. Docassemble variables should be:
1. Short
1. Readable (ie., usually you should spell out a word without abbreviations).
1. Lowercase
1. Include `_` to separate words.
1. Cannot begin with a number but may include a number.

If you get stuck, look at the `interview-basic.yml` file for one approach to solving the problem.

### Writing interview questions
We will need to create an interview screen to gather all of the information. We could create a single page that includes all of the variables. This might be very messy and hard to read. A better practice is to group the related questions together. Try it on your own first. Sketch out 5-6 screens to start.

A logical grouping might be:
1. The tenant's name, address, and phone number
2. The court name and county
3. The landlord's name
4. The bases for dismissal
5. The service date and type.

If you get stuck, look at the `interview-basic.yml` file for one approach to solving the problem.

### Putting it all together

### Applying legal reasoning
You may have wondered how exactly the end user of the interview is supposed to know the bases for dismissal. One of the most powerful features of a guided interview platform like Docassemble is the possibility to simulate a "lawyer in a box" at the other end of the interview.

Here are the basic legal rules necessary to understand each basis for dismissal:

1. A landlord cannot terminate a tenancy with a 14 day notice to quit if the tenant paid all rent owed before the landlord sent the notice.
1. If the tenant has a lease, the tenant can "cure" the notice to quit by paying all of the rent owed on or before the "answer date". If the tenant has a tenancy at will (month to month), the tenant can "cure" the notice to quit by paying all rent owed on or before 10 days of receiving the notice to quit.
1. If the landlord accepted any rent after sending the notice to quit without including a "reservation of rights" in the notice to quit or immediately when accepting the rent, the termination may be "waived". A reservation of rights looks like this: "any payments will be accepted for use and occupancy only and will not reinstate the tenancy."

A highly readable primer on Massachusetts Eviction law can be found here: http://www.masslegalhelp.org/legal-tactics. Check out [Chapter 12](http://www.masslegalhelp.org/housing/lt1-chapter-12-evictions.pdf), the section titled "Stopping an Eviction Before a Trial" to see more detailed information about the basic rules above.

#### Break the information required into smaller logical elements
Given the rules above, what additional information do we need to know to decide if any of the three bases for dismissal apply? Try it on your own first. When you have finished, you should have a list that looks like the list below:

* What was the answer date?
* Does the tenant have a tenancy by lease or at will?
* When did the tenant receive the notice to quit?
* When did the tenant last pay rent?
* Did the tenant pay the full amount of rent owed?
* Did the notice to quit contain a reservation of rights?

Remove the interview section that asks directly if the bases for dismissal apply. Instead, we will create new interview screens that ask the facts listed above. Try it on your own first.

If you get stuck, look at the file `interview-logic.yml` for one approach to solving the problem.

#### Apply the logical rules to our interview
Notice that we do not need to make any changes to our template to add this additional logic. A `code` block in Docassemble can set a variable based on the value of another variable using a logical `if` statement.

We can include all of our logical rules in a single code block. To get you started, below is an example logical block to test one scenario, a tenant who has a lease curing the notice to quit by paying all rent due sometime before the Answer date. 

```yaml
---
code: |
  if tenancy_type == 'lease':
    if tenant_paid_all_rent_due and tenant_pay_date <= answer_date:
      tenant_cured = True
    else:
      tenant_cured = False
```

Try completing the exercise for the remaining logical scenarios: a tenant who has a tenancy at will, a tenant who paid before receiving the notice to quit, and a tenant whose landlord waived the notice to quit by accepting rent without a reservation of rights.

# Conclusion
We hope that this tutorial will help you develop your own guided interviews in Docassemble!
