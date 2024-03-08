## Survey Microservices Project
This is a learning project primarily to see if a Platform as a Service (PaaS) ecosystem can serve as a solution for a basic survey submission requirement.  

The user experience is simple: download a survey in PDF format, fill it out offline, and upload it. Resources deployed in Azure will utilize Artificial Intelligence (AI) to process the survey answers. Additional resources will persist those answers in a database. 

Reviewers of surveys will be able to read survey answers without having to download the submitted PDF files. 

Imagine if this project was organized like a long-form version of interactive lab with business and technical requirements.

### Business Requirements
- As a submitter, I want to fill out a PDF offline and submit it
- As a reviewer, I want to review the data of surveys without downloading and reviewing pdfs
- As an Application Admin, I want to be notified when a Survey has been stored in the database after submission

### Technical Requirements
- Responsibilities should be divided (i.e. front-end application should not contain database logic)
- Must contain an AI component
- Use PaaS resources exclusively
- Maximize cost savings even if it means sacrificing performance (personally trying not to spend a lot of money on a side project 😉)
- No sensitive information exposed in apps or pipelines

### Not Required
- The UI does not need to be styled (form over function)
- Code perfection is not a goal
- Security, although important, is not a requirement (i.e. VNets, Private IP's, etc.)

## Github Repositories (Imported from Azure DevOps)
- [Database Schema Project](https://github.com/Survey-2024/SurveyDB)
- [Front End Blazor Application (coming soon)]()
- [API Application (coming soon)]()
- [Function Application (coming soon)]()

## Azure DevOps Project
[Survey ADO (private)](https://dev.azure.com/cjdaley/Survey/) 



<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
