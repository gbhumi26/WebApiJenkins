pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/gbhumi26/WebApiJenkins'
            }
        }
        stage('Your Other Stages...') { // Add your other build, test, etc. stages here
            steps {
                // ... your other steps ...
            }
        }
        stage('Deploy to Azure (Example)') { // Example stage where you might use Azure credentials
            steps {
                withCredentials([azureServicePrincipal('azure-service-principal')]) {
                    script {
                        echo "Tenant ID: $AZURE_CREDENTIALS_TEN"
                        echo "Client ID: $AZURE_CREDENTIALS_USR"
                        echo "Client Secret: $AZURE_CREDENTIALS_PSW"

                        // Now you can use these variables in your Azure CLI or Terraform commands
                        // Example Azure CLI login:
                        // sh "az login --service-principal -u $AZURE_CREDENTIALS_USR -p $AZURE_CREDENTIALS_PSW --tenant $AZURE_CREDENTIALS_TEN"

                        // Example Terraform command (assuming you're in the terraform directory):
                        // sh "terraform init -backend-config=\"tenant_id=$AZURE_CREDENTIALS_TEN\" -backend-config=\"subscription_id=$AZURE_CREDENTIALS_SID\" -backend-config=\"client_id=$AZURE_CREDENTIALS_USR\" -backend-config=\"client_secret=$AZURE_CREDENTIALS_PSW\""
                    }
                }
            }
        }
    }
}
