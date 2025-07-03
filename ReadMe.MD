# **Anaplan Production Deployment – Production Account

*Prerequisites for Anaplan Production Deployment:

Create the TFE (Terraform Enterprise) workspace and define the required variables.

Create the Harness pipeline and raise a change request for deployment.

Ensure the source code is merged from the release branch to the prod branch.

Once the prerequisites are completed, you can proceed with the Anaplan deployment by running the respective pipeline in Harness.

#*Note:
If any pipeline executions were performed earlier for testing, ensure all previously created resources are deleted before starting the actual deployment process.

#*Deployment Process:

During pipeline execution, security and compliance scan checks will be performed.

Once the scans pass, the pipeline will pause for manual approval.

After manual approval, a Change Request (CR) validation check will be triggered.

Ensure the App Code name is consistent across both TFE and Harness.
A mismatch in App Code between TFE and Harness will cause the CR validation to fail.

#* If there is a mismatch in App Code:

Submit an Intact form to the TFE team requesting the App Code on TFE to be updated to match the Harness pipeline.

The App Code must be identical on both TFE and Harness.

Once the CR validation passes, the pipeline proceeds to the Terraform apply stage.

# **Post-Deployment Manual Tasks:

After successful execution of the pipeline:

Log in to the Anaplan Production Account and create the secret key and password.

Log in to the AWS Production Root Account and create the data export configuration.

Verify that all necessary resources are created and configured in both the Anaplan Prod Account and the Production Root Account.

# **Issue Encountered and Resolution:

During deployment, an App Code mismatch was observed:

In the Harness pipeline, the App Code was set to AFP.

In TFE, the App Code was mistakenly created as AFPOPS.

This mismatch caused the CR validation to fail.

# **Resolution:

An Intact form was submitted to the TFE team to update the App Code from AFPOPS to AFP.

After the correction, the deployment proceeded successfully.
