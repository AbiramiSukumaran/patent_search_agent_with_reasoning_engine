# patent_search_agent_with_reasoning_engine

## CORRECTION:

Remember to run these permissions in the second last cell before you try out the deployed Reasoning ENGINE!!!

PROJECT_NUMBER = !gcloud projects describe {PROJECT_ID} --format="value(projectNumber)"
SERVICE_ACCOUNT = f"service-{PROJECT_NUMBER[0]}@gcp-sa-aiplatform-re.iam.gserviceaccount.com"

# Grant IAM Permissions for database-user authentication
!gcloud projects add-iam-policy-binding {PROJECT_ID} \
    --member=serviceAccount:{SERVICE_ACCOUNT} \
    --role=roles/alloydb.databaseUser

# Grant IAM permissions to access AlloyDB instances
!gcloud projects add-iam-policy-binding {PROJECT_ID} \
    --member=serviceAccount:{SERVICE_ACCOUNT} \
    --role=roles/alloydb.client

# Grant IAM permissions to access AI Platform services
!gcloud projects add-iam-policy-binding {PROJECT_ID} \
    --member=serviceAccount:{SERVICE_ACCOUNT}  \
    --role=roles/aiplatform.user

# Grant IAM permissions for service usage consumer role
!gcloud projects add-iam-policy-binding {PROJECT_ID} \
    --member=serviceAccount:{SERVICE_ACCOUNT}  \
    --role=roles/serviceusage.serviceUsageConsumer
