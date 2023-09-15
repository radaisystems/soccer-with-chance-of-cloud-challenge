# The Challenge
Platform engineering extends beyond coding and encompasses cloud integration. We require you to create a program that can be executed both via the command line and in a cloud environment. This program's purpose is to compute the ranking table for a soccer league.

## Table of contents
- [The Challenge](#the-challenge)
  * [Expected input and output](#expected-input-and-output)
  * [The rules](#the-rules)
  * [Guidelines](#guidelines)
    + [After you finish](#after-you-finish)
  * [What to send back to our team](#what-to-send-back-to-our-team)
    + [Platform support](#platform-support)
    + [What to expect afterwards](#what-to-expect-afterwards)

# Cloud

Begin with cloud operations. Write either a bash script, use a cloud platform tool like Terraform, or a combination of both to achieve the following tasks

AWS credentials will be sent to you via email for use on this part of the project.  Please do not share these credentials with anyone else.  You will only have access to Access Keys for the duration of the challenge.

- Create an S3 bucket called `soccer-with-chance-of-cloud-challenge-<your name>`
- Send the `data/sample-input.txt` file to the root of the bucket
- Delete the data/simple-input.txt file from your local copy of the repository
- Your bucket should reflect using industry standard security practices for storing private data

# Coding

You can find the [data/sample-input.txt](data/sample-input.txt) and [expected-output.txt](expected-output.txt) files in this repository

The input contains results of games played, one per line. See `data/sample-input.txt` for details. The output of your completed script should be ordered from most to least points, following the format specified in `expected-output.txt`.

You can expect that the input will be well-formed. There is no need to add
special handling for malformed input files.

## The rules

In this league, a draw (tie) is worth 1 point and a win is worth 3 points. A loss is worth 0 points. If two or more teams have the same number of points, they should have the same rank and be printed in alphabetical order (as in the tie for 3rd place in the sample data). Ranks are assigned according to [standard competition (1224) ranking](https://en.wikipedia.org/wiki/Ranking#Standard_competition_ranking_(%221224%22_ranking)).

We expect the resulting output of the provided `data/sample-input.txt` file to *exactly match the contents* of `expected-output.txt`.

## Guidelines

For the programming languages allowed we would prefer that you use Python. If Python is not a programming language that you use often, please choose a language that is both comfortable for you and suited to the task. However _we would be very impress_ if you are able to submit the challenge in a pythonic fashion (don't worry we would be rating your submission keeping this in mind!).

Your script will need to download the sample-input.txt file from the S3 bucket.  That file should be downloaded if it does not exist locally or was last downloaded the previous day.

Your solution should be able to be run from the command line. Please include appropriate scripts and instructions for running your application and your tests.

If you use other libraries installed by a common package manager (pip, poetry, npm, gradle, etc.), please include a formatted list of packes, it is not necessary to commit the installed packages.

We write automated tests and *we would like you to do so as well*.

We appreciate well factored, object-oriented or functional designs.

We request that you spend no more than a few hours on this portion of the interview ( <= 3 hours is what we expect).

You should use optimal security practices when working with the AWS credentials.  Please do not share these credentials with anyone else.

# Bonus Points

In this stage, we'll transition the script from the command line to the cloud. Please backup your current script before proceeding. You will need to submit both scripts. Modify your existing Terraform, bash, or equivalent to implement the following AWS adjustments. Also, ensure your revised script meets these specifications:

- Develop a Lambda and upload the modified script to it.
- Establish an SNS Topic and add your email address as a subscriber for testing. Remember to confirm the subscription.

The revised script should be executable from AWS Lambda, with all output directed to the email associated with the SNS Topic. Adjust as necessary and update your Terraform, bash, or equivalent to mirror these alterations

Your supervisor is pleased with your progress and would like to see this service taken to the next level.  Write 1-2 paragraphs with a diagram about how you would make this a highly available service that could be run on a regular basis and receive regular code changes.  Use any format for the writeup that you feel comfortable with so long as it can be packaged in a zip with the test of your submission.

# Site Reliability Engineer (SRE) Tasks

The following should only be handled by candidates of the SRE role.  If you are not applying for the SRE role, please ignore this section.

An SRE requires the ability to write code to interact with AWS infrastructure.  You must complete the Bonus Points section above before continuing

"Craft a script that provides an interactive command-line interface for the user. This script should:

- Display a menu of choices to the user.
- Include an option to execute the Lambda script mentioned in the prior section.
- Provide an option to send a test email via the SNS Topic.
- Feature an option to run the local tests you finished in a previous step.
- Allow for exiting the script.

### After you finish

- Please document any steps necessary to run your solution and your tests.
- Please take 10 minutes to review your submission and list a few areas that would benefit from more time and attention.

## What to send back to our team

Please send an email back to your point of contact with:

- the code you used to calculate the rankings
- your test suite code
- simple instructions on how to install and use your code
- the amount of time you spent on the project
- the list of improvements you would make

> You can send us the submission in the form of a tarball or a zip file

### Platform support

This will be run in a unix-ish environment (OS X or Linux).
Please use platform-agnostic constructs where possible (line-endings and file-path-separators are two problematic areas).

### What to expect afterwards

Once you have sent us your project, we will review the code with our team members and rate it appropiately.
If everything looks fine, we would like to have a code review interview with you where we will be going over what you sent us, as well as requesting a few changes in the code to see if the output can be altered. An example of what you can be expecting can be seen in this documentation: [goal-differential-instructions.md](goal-differential-instructions.md)
