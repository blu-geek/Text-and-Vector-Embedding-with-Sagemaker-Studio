# Text-and-Vector-Embedding-with-Sagemaker-Studio
Text and Vector Embedding using Amazon Titan in Amazon Bedrock

Architecture

<img width="739" alt="Screenshot 2025-01-16 at 15 40 05" src="https://github.com/user-attachments/assets/bf4b3d4b-cab4-46cc-b2bf-25c2aad779ba" />

# Flow

1. The user provides a question using a Streamlit web application.
2. The web application invokes the Amazon API Gateway endpoint’s representational state transfer API.
3. API Gateway invokes an AWS Lambda function.
4. The function invokes the SageMaker endpoint to convert the user’s question into embeddings.
5. The function invokes an OpenSearch Service API to find documents similar to the user’s question.
6. The function creates a prompt, with the user’s query and the similar documents as context. It then asks the SageMaker endpoint to generate a response.
7. The Lambda function provides the response to API Gateway.
8. API Gateway provides the response to the Streamlit application.
9. The user can view the response on the Streamlit application.




# Activity Guide: Text and Vector Embedding with Amazon Titan in SageMaker Studio

1. Set Up SageMaker Domain (Amazon SageMaker Studio)
- Create Domain:
Open the SageMaker Console, navigate to Domains, and click Create Domain.
- Configure Single User:
Select Set-up for single user and click Setup. Wait for approximately 10 minutes for the setup to complete.

2. Launch SageMaker Studio (Amazon SageMaker Studio)
- Access Studio:
Navigate to User Profiles, click Launch next to your profile, and open SageMaker Studio.
- Skip Tour:
Click Skip tour for now if prompted.
- Open JupyterLab:
Click on the JupyterLab icon in the left panel to launch the notebook environment.

3. Configure JupyterLab Environment (JupyterLab)
- Create Space:
Click + Create JupyterLab Space, name it My-GenAI-Space, and click Run space.
- Upload Files:
Upload the zipped lab files from your local system.
- Open a terminal in JupyterLab and run the following commands:
unzip GenAI_Demos.zip ( Grants you access to the notebook used for this activity which i have shared in my repository)
- Verify Files:
Confirm the unzipped files appear in the navigation panel.

4. Adjust Environment Settings (JupyterLab)
- Disable Code Diagnostics:
Navigate to Settings > Settings Editor > Code Diagnostics and set it to Disable.
- Edit JSON Settings:
Open Settings > JSON Settings Editor, delete the existing text in User Preferences, and replace it with:
{
    "language_servers": {
        "pylsp": {
            "serverSettings": {
                "pylsp.plugins.pycodestyle.enabled": false
            }
        }
    }
}
Save Changes:
Click Save and close all tabs.
Note: The steps in 4 above may not be neccessary based on priorities. Speed of execution was key over readablity or documentation.

5. Run Jupyter Notebook (Amazon SageMaker)
- Open Notebook:
- Run the notebook cells sequentially to:
Generate text embeddings.
Perform similarity testing.
- Test with Input Queries:
Use inputs like What is the price of iPhone 15? or What is the price of product number 5723? to evaluate the model's capabilities.

6. Clean Up Resources
- Delete Jupyter Space (Amazon SageMaker Studio):
Stop the running Jupyter space and delete it under the Actions column in the SageMaker Studio tab.
- Delete S3 Bucket (Amazon S3):
Navigate to the S3 Console, locate the bucket used, and delete it after emptying.

8. Troubleshooting
- Issue: AccessDeniedException during notebook execution:
Check: Ensure the Amazon Titan Embed Text v1 model is deployed in the same region as SageMaker Studio.
Fix: Deploy the model as described in the prerequisites.

9. Summary
Successfully generated text embeddings and performed similarity testing using Amazon Titan in SageMaker Studio.
Learned how to streamline workflows and manage resources in AWS for NLP projects.
