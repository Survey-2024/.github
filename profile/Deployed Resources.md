# Survey Microservices Resources Inventory 
This is a list containing all the resources deployed into Azure to support this project.

1. [Identity](#identity)
1. [Data/Storage](#datastorage)
1. [Applications](#applications)
1. [AI](#ai)
1. [Monitoring](#monitoring)
1. [Consumption/Billing](#consumptionbilling)
1. [API Management](#api-management)
1. [Configuration](#configuration)
1. [Security](#security)
1. [Communication](#communication)

​ 
## Identity 
### Service Principals (and App Registrations) 
1. SurveySP 
    1. Service Principal granted read roles to a Key Vault resource 
        1. Used as an authenticated identity to read Key Vault resources and use those secrets as variables within pipelines 
        1. Bound to an Azure DevOps Service Connection named Survey Key Vault 
        1. Granted Role of Key Vault Secrets User on the kv-surveycreds Key Vault 
1. SurveyPipelineSP 
    1. Used as an authenticated identity to deploy resources into Azure via Azure  

### Managed Identities 
1. ai-docreader 
    1. Azure Role Assignments  
        1.None (TBD if resource is required) 
1. SurveyApiCjd 
    1. Azure Role Assignments 
      1. Key Vault Secrets User (kv-surveycreds) 
      1. Azure Service Bus Data Sender (rg-docreader) 
1. fn-docparser 
    1. Azure Role Assignments 
        1. Key Vault Secrets User (kv-surveycreds) 
1. SurveyDocUploader 
    1. Azure Role Assignments 
        1. Key Vault Secrets User (kv-surveycreds) 
        1. Azure Service Bus Data Receiver (rg-docreader) 

## Data/Storage 
1. SQL Server 
    1. Sqlserver0978 
1. SQL database 
    1. DBSurveyProject 
1. Storage Account 
    1. stdocreader 
        1. Blob Containers 
            1. Processed 
                1. Documents processed by AI Document Intelligence (archival container) 
            1. Templates 
                1. Sample Documents downloadable by front end application 
            1. Training 
                1. Sample Documents submitted to AI Document Intelligence Studio for marking to train the AI model 
            1. Uploads 
                1. Temporary storage for user uploaded surveys prior to processing (normally should be empty) 

## Applications 
1. SurveyDB (not an App Service, not deployed in Azure) 
    1. Visual Studio SQL Server Database Project  
        1. Defines database schema and includes table seeds 
        1. Pipeline updates Sql Database deployed in Azure 
1. SurveyApiCjd 
    1. Facilitates communication between SQL Database (DBSurveyProject) and other applications 
1. SurveyDocUploader 
    1. Front-End Application authored in Blazor where users upload PDF surveys and reviewers analyze survey data 
1. Fn-docparser 
    1. Serverless application that acts as an orchestrator between the front-end application and the database API.  
    1. Polls for new uploads, sends PDFs to AI Document Intelligence, massages and sends results to database API. 

## AI 
1. Ai-docreader 
    1. Azure Resource that manages the Optical Character Recognition (OCR) of submitted PDFs  

## Monitoring 
1. Application Insights 
    1. Fn-docparser-i 
    1. SurveyAiCjd-i 
    1. SurveyDocUploader-i 
    1. Log Analytics Workspace 
        1. DefaultWorkspace-146f2515-80c9-4a78-ae5d-452e9a3d7255-EUS 

## Consumption/Billing 
1. App Service Plans 
    1. Asp-docreader 
        1. Resource scale for 
            1. SurveyDocUploader 
            1. SurveyApCjd 
    1. ASP-rgdocreader-90e7 
        1. Consumption plan for fn-docparser 

## API Management 
1. SurveyApiManagement 
    1. Allows test runs against api methods 

## Configuration 
1. Appconfig-survey 
    1. Stores Key Vault References for consumption within applications 

## Security 
1. Kv-surveycreds 
    1. Contains secrets for resources in ecosystem 
    1. Secrets User RBAC identities: 
        1. Apps 
            1. Fn-docparser 
            1. SurveyApiCjd 
            1. SurveyDocUploader 
        1. Identities 
            1. SurveyPipelineSP
                1. Required to Generate OpenAI Spec Document (swagger.json) in the API DevOps pipeline for deployment to API Management 
            1. SurveySP 

## Communication 
1. Sbsurvey 
    1. Service Bus Namespace used to send notifications between API app and Front-end App 
