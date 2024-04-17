## Survey Microservices Project
This is a learning project where a deployed Platform as a Service (PaaS) ecosystem serves as a solution for a survey submission/consumption scenario.  

Survey submitters download a survey in PDF format, fill it out offline, and upload it. An Artificial Intelligence (AI) custom-trained machine-learning model extracts the answers and persists them in a database. Survey reviewers can read survey answers without having to download and read the submitted PDF files.

For any inquiries or demo requests, feel free to reach out either here or [LinkedIn](https://www.linkedin.com/in/cjd78/)!


![Survey Video](https://github.com/Survey-2024/.github/assets/13341430/3b8fd52f-78a3-4b75-a165-eabf0e2e43a6)


Imagine if this project was organized like a long-form version of interactive lab with business and technical requirements.

### Business Requirements
- As a submitter, I want to fill out a PDF offline and submit it
- As a reviewer, I want to review the data of surveys without downloading and reviewing pdfs
- As an Application Admin, I want to be notified when a Survey has been stored in the database after submission

### Technical Requirements
- Responsibilities should be divided (i.e. front-end application should not contain database logic)
- Must contain an AI component (because it's the hotness)
- Use PaaS resources exclusively
- No sensitive information exposed in apps or pipelines (i.e. resource access keys)
- Minimize costs even if it means sacrificing performance (personally trying not to spend a lot of money on a side project 😉)

### Not Required or Out of Scope
- The UI does not need to be styled (form over function)
- Code perfection is not a goal (i.e. not trying to catch all error conditions like we would in a professional effort)
- Infrastructural Security, although important, is not a requirement (i.e. VNets, Private IP's, etc.)
- Security Roles not required, (i.e. all users will receive a notification when a survey is stored with a link to review)
- Infrastructure as Code (IaC) (i.e. resources can be deployed via portal)

## Github Repositories (Imported from Azure DevOps)
- [Database Schema Project](https://github.com/Survey-2024/SurveyDB)
- [API Application](https://github.com/Survey-2024/SurveyApi)
- [Front End Blazor Application](https://github.com/Survey-2024/SurveyFrontEnd)
- [Serverless Function Application](https://github.com/Survey-2024/DocParser)

## Azure DevOps Project
This is the "live" project where the build/deploy pipelines are operational. Also, all the work management is there via Boards.

[Survey ADO (private)](https://dev.azure.com/cjdaley/Survey/) 

## Flow
1. Front-end app - User downloads template survey pdf to fill out offline
2. Front-end app - User uploads survey that is stored in a Storage Account
3. Function App - Processes the document
   1. Sends survey to Document Intelligence for json extraction
   2. Archives Survey
   3. Stores data via API app call
 4. API app after storing data sends a message to Service Bus for consumption
 5. Front-end app - Consumes Service Bus message
 6. Front-end app - User reviews survey content

![image](https://github.com/Survey-2024/.github/assets/13341430/b3ab7dac-b419-48b3-8a96-2db35df94565)

## Sensitive Information
Sensitive Information (credentialed endpoints, database account passwords, etc) are stored in Key Vault. The App Configuration resource pulls data from Key Vault and made accessible to all applications via a single endpoint.

![image](https://github.com/Survey-2024/.github/assets/13341430/7b24e5a1-e585-4ca7-9910-a90fe95aa896)

## Additional Resources
- Application Insights resources are deployed for monitoring
- Log Analytics workspace centralizes monitoring
- API Management service for on-demand API calls

## CI/CD Pipelines
All applications have pipelines that build and deploy to Azure resources.

![image](https://github.com/Survey-2024/.github/assets/13341430/9eec969e-6829-4738-beec-b16a1cc2a5ef)

<br/><br/>

## List of Resources Deployed in Azure

[Resources Inventory](https://github.com/Survey-2024/.github/blob/bcb4309fbc2b98641f54a27c54d27531cae353fc/profile/Deployed%20Resources.md)

<br/><br/>

### ER Diagram
<img width="600px" alt="Database Entity Relationship Diagram" src="https://github.com/Survey-2024/.github/assets/13341430/6b4f1bd5-e47f-4939-8594-fc324bd7d302" />

<br/><br/>

### Resources Used
#### Tools
- Azure Document Intelligence Studio (https://documentintelligence.ai.azure.com/) for model training
- Azure Data Studio for initial database design
- Visual Studio for application coding
    - Database project for schema updates
    - API
    - Blazor Application
    - Function (serverless) Application
 - Visual Studio Code to run terminal Azure CLI scripts to test scenarios prior to CD pipeline implementation
 - Azure DevOps for work management, code repositories, CI/CD pipelines
 - Azure Portal for resource deployment
 - Github for public documentation, copies of repositories
 - Github Desktop for initial pushes
#### Diagramming
- https://lucid.app/ (Flows)
- https://github.com/R0tenur/visualization (ERD generated by Schema Visualization extension in Azure Data Studio)
#### Media
- https://www.canva.com/ (Survey Icon)
- https://recordscreen.io/ (Video Capture)
- https://www.veed.io/ (Video Editing / Export to GIF)

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
