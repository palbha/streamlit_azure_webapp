# demo-streamlit-azure
- Demo repo to deploy Streamlit private repo to Azure service.
- Note: This guideline is written on August 2023. Any changing or deprecation might be happened in the future. 


## Deployment Guideline


### Step 1: Basics Section
1. Search **App Serives** and click it. Then click `Create` and choose `Web App`.
2. Choose existed Resource Group (`rg_invoke`)
3. Write app name. Please ensure the name is descriptive as possible. ie. `analytics-dashboard-web-app`
4. For Publish, choose `Code` (if you have container, choose `Container`)
5. Choose runtime stack (`Python`). Please ensure the Python version is similar to the Python version that you used on local development. 
6. Select region (`Southeast Asia`)
7. Select operating system (Linux is recommended)
8. Create Linux-plan name. Please ensure the name is descriptive as possible. ie `linux-analytics`
9. Choose pricing plan for compute resources. Refer experience developer/lead to get some advice on the choice. 
10. Ignore *Zone redundancy*. 
11. Move to Step 2.

### Step 2: Deployment 
1. On the same page, click **Deployment** tab. 
2. Click **Enable** for Continuous deployment.
3. On Github account, link to your Github account.
4. Choose organization (`INVOKE-Analytics`)
5. Select project repository name. 
6. Select branch to deploy.
7. Click **Review + create**. Please ensure all the description is correct following to your deployment plan. 
8. Click **Create**.
9. Move to Step 3. 

### Step 3: Configuration
1. Click your web-app name in App Service. 
2. Click **Configuration** (Under settings)
3. Click **General settings**
4. Ensure the stack is Python, major version and minor version is correct.
5. Insert the following line for startup command. The `main.py` is referred to the top script to deploy.  
```cmd
python -m streamlit run main.py --server.port 8000 --server.address 0.0.0.0
```
6. Click **Save**. 
7. Move to step 4. 

### Step 4: Github Actions
1. Open your project repo on Github. 
2. You will see there is `.github/workflows` directory created by Azure for the CI/CD.
3. Click **Actions**.
4. A **workflow** should be running. 
5. Wait until the process is finished. 
6. If the workflow failed, rerun the workflow. 
7. If the workflow succeed, click the link return by the workflow. 
8. You will be redirected to your Streamlit app. 
9. Deployment finished. 
10. Congratulation you have deployed your app on Azure!