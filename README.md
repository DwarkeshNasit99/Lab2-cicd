# Jenkins CI/CD Pipeline Demo

This is a simple Python Flask application that demonstrates CI/CD pipeline integration between GitHub and Jenkins.

## Project Structure
- `app.py`: Main Flask application
- `test_app.py`: Unit tests for the application
- `requirements.txt`: Python dependencies
- `Jenkinsfile`: Jenkins pipeline configuration

## Local Setup
1. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the application:
   ```bash
   python app.py
   ```

4. Run tests:
   ```bash
   python -m pytest test_app.py -v
   ```

## Jenkins Pipeline
The pipeline includes the following stages:
1. Checkout: Clones the repository
2. Setup Python: Creates virtual environment and installs dependencies
3. Build: Compiles Python files
4. Test: Runs unit tests
5. Deploy: Placeholder for deployment stage
6. Notification: Sends email notifications on build status

## CI/CD Configuration
This project uses GitHub webhooks to trigger Jenkins builds automatically when changes are pushed to the repository.

### Jenkins Configuration Steps:
1. Create a new Pipeline job in Jenkins
2. Configure the job to use the Jenkinsfile from SCM
3. Set up GitHub webhook in your repository settings
4. Configure email notifications in Jenkins

### GitHub Webhook Setup:
1. Go to your repository settings
2. Navigate to Webhooks
3. Add webhook with your Jenkins URL (e.g., http://your-jenkins-url/github-webhook/)
4. Select content type as application/json
5. Choose events to trigger the webhook (at minimum, push events) 