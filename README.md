
# Azure Web Apps Flask Deployment

This project demonstrates the deployment of a simple Flask application to Azure Web Apps using GitHub Actions for CI/CD.

## Project Structure

- `app.py`: Contains the Flask application code
- `requirements.txt`: Lists the Python dependencies
- `.github/workflows/azure-webapps-python.yml`: GitHub Actions workflow for CI/CD

## Flask Application

The application consists of a single endpoint that returns "Hello, Azure Web Apps!" when accessed.

## Deployment Instructions

### Prerequisites

- An Azure account with an active subscription
- A GitHub account

### Steps

1. Fork or clone this repository to your GitHub account.

2. Create an Azure Web App:
   - Log in to the Azure portal
   - Create a new Web App resource
   - Fill in the required details:
      - Subscription: Your Azure subscription.
      - Resource Group: Create a new one or use an existing one.
      - Name: Unique name for your web app.
      - Publish: Choose "Code".
      - Runtime Stack: Select Python (choose the version that matches your application. We are using `Python 3.9` ).
      - Region: Choose a region close to you (We are using `West India` in our case).

3. Configure deployment from GitHub:
   - In the Azure Web App settings, go to "Deployment Center"
   - Choose GitHub as the source
   - Select your repository and branch
   - Choose GitHub Actions as the build provider

4. Set up deployment credentials:
   - In your Azure Web App, go to "Overview" and click on "Get publish profile"
   - Copy the contents of the downloaded file
   - In your GitHub repository settings, go to "Secrets and variables" > "Actions"
   - Create a new repository secret named `AZURE_WEBAPP_PUBLISH_PROFILE` and paste the publish profile content

5. Update the GitHub Actions workflow:
   - Open `.github/workflows/azure-webapps-python.yml`
   - Replace `flask-app` with your actual Azure Web App name

6. Commit and push your changes:
   - This will trigger the GitHub Actions workflow and deploy your application

7. Verify the deployment:
   - Once the GitHub Actions workflow completes, visit your Azure Web App URL
   - You should see the message "Hello, Azure Web Apps!"

## Continuous Integration/Continuous Deployment (CI/CD)

This project uses GitHub Actions for CI/CD. The workflow is defined in `.github/workflows/azure-webapps-python.yml`. It automatically deploys the application to Azure Web Apps whenever changes are pushed to the main branch.

## Troubleshooting

If you encounter any issues during deployment:
- Check the GitHub Actions logs for any error messages
- Review the Azure Web App logs in the Azure portal
- Ensure all environment variables and secrets are correctly set

## Additional Notes

- This project uses Python 3.9. If you need to use a different version, update it in the GitHub Actions workflow file.
- Make sure to keep your `AZURE_WEBAPP_PUBLISH_PROFILE` secret up to date. If you regenerate your publish profile, you'll need to update the secret in GitHub.

## Contributing

Feel free to submit issues or pull requests if you have suggestions for improvements or find any bugs.
