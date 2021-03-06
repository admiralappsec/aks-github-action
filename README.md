# aks-contrast-security-github-action

This github action builds and deploys a java application to the Azure Kubernetes Service (AKS) with a Contrast Security Java Agent.

## Prerequisites

- An Azure Service Principle with enough permissions to: 
    - Deploy an application to Azure Kubernetes Service (AKS)
    - Deploy a volume
    - Create a secret 
- A valid Contrast Security account
- Prepopulated Contrast Security and Azure JSON objects - details within 'Inputs' section

## Inputs
- `azure-credentials-file`
  - Description: 'The configuration file contents for Azure-specific logins, regions, etc...'
  - REQUIRED: true
  - Default: No Default Value
  - Example:
    ```sh
    {
      "azure_application_id": "xxxxx",
      "azure_tenant_id": "xxxxx",
      "azure_client_secret": "xxxxx",
      "azure_subscription_id": "xxxxx",
      "azure_resource_group_name": "xxxxx",
      "azure_region": "xxxxx",
      "azure_container_registry": "xxxxx"
    }
    ```
- `contrast-security-credentials-file`
  - Description: 'The configuration file contents for the Contrast Security Java Agent - used to communication with Contrast Security Team Server'
  - REQUIRED: true
  - Default: No Default Value
  - Example:
    ```sh
    {
    "contrast_api_url": "xxxxx",
    "contrast_api_username": "xxxxx",
    "contrast_api_api_key": "xxxxx",
    "contrast_api_service_key": "xxxxx",
    "contrast_agent_java_standalone_app_name": "xxxxx",
    "contrast_application_version": "xxxxx"
    }
    ```
- `application-manifest`
  - Description: 'Application manifest file location required for kubernetes deployment'
  - REQUIRED: true
  - Default: No Default Value
- `application-dockerfile`
  - Description: 'dockerfile location required for docker build'
  - REQUIRED: true
  - Default: No Default Value
- `application-output-image-name-tag:
  - Description: 'output image name/tag that will be deployed to kubernetes cluster'
  - REQUIRED: true
  - Default: No Default Value
- `cluster-name`
  - Description: 'aks cluster name'
  - REQUIRED: true
  - Default: No Default Value
- `application-artifact`
  - Description: 'artifacts location associated with the docker build'
  - REQUIRED: false
  - Default: No Default Value

## Documentation

Can be found at these links:

> Note: `This section` is to be updated...

## Example Use

```sh
- name: Contrast Security Azure Kubernetes Service Deployment
        uses: admiralappsec/aks-github-action@v1
        id: contrast-deployment
        with:
          contrast-security-credentials-file: ${{ secrets.CONTRAST_CREDS_FILE }}
          azure-credentials-file: ${{ secrets.AZURE_CREDS_FILE }}
          application-manifest: ${{ env.APPLICATION_MANIFEST }}
          application-dockerfile: ${{ env.APPLICATION_DOCKERFILE }}
          application-output-image-name-tag: ${{ env.IMAGE_NAME_TAG }}
          cluster-name: ${{ env.CLUSTER_NAME }}
          application-artifact: ${{ env.APPLICATION_ARTIFACT }}
```

## Development

> Note: `This section` is to be updated...
