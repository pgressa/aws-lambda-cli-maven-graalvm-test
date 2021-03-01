## Micronaut 2.4.0-SNAPSHOT Documentation

- [User Guide](https://docs.micronaut.io/snapshot/guide/index.html)
- [API Reference](https://docs.micronaut.io/snapshot/api/index.html)
- [Configuration Reference](https://docs.micronaut.io/snapshot/guide/configurationreference.html)
- [Micronaut Guides](https://guides.micronaut.io/index.html)
---

## Handler

[AWS Lambda Handler](https://docs.aws.amazon.com/lambda/latest/dg/java-handler.html)

Handler: io.micronaut.function.aws.proxy.MicronautLambdaHandler

## AWS Lambda GraalVM Workflow (CLI)

Workflow file: [`.github/workflows/aws-lambda-cli-graalvm.yml`](.github/workflows/aws-lambda-cli-graalvm.yml)

### Workflow description
For pushes to the `master` branch, the workflow will:
1. Setup the build environment with respect to the selected java/graalvm version.
2. Login to Docker registry.
3. Login to [Azure Command-Line Interface](https://docs.microsoft.com/cs-cz/cli/azure/).
4. Build, tag and push Docker image with Micronaut application to the Docker Registry.
5. Deploy to [Azure Container Instances](https://docs.microsoft.com/cs-cz/azure/container-instances/).

### Dependencies on other GitHub Actions
- [Login to Docker Registry `docker/login`](https://github.com/docker/login-action)
- [Setup GraalVM `DeLaGuardo/setup-graalvm`](https://github.com/DeLaGuardo/setup-graalvm)
- [Setup Azure CLI `azure/login`](https://github.com/Azure/login)

### Setup
Add the following GitHub secrets:

| Name | Description |
| ---- | ----------- |
| AWS_ACCESS_KEY_ID | AWS Access Key Id. |
| AWS_SECRET_ACCESS_KEY | AWS Secret Access Key. |
| AWS_ROLE_ARN | AWS Role ARN under which the Lambda function runs. |

The workflow file also contains additional configuration options that are now configured to:

| Name | Description | Default value |
| ---- | ----------- | ------------- |
| AZURE_LOCATION | Location where the Container Instance will be created. See [Resource availability for Azure Container Instances in Azure regions](https://docs.microsoft.com/en-us/azure//container-instances/container-instances-region-availability) to find out what regions are supported. | `westeurope` |
| AZURE_DNS_LABEL | The dns name label for container group with public IP. | `aws-lambda-cli-maven-graalvm-test` |


### Verification
Call the rest api endpoint `[AZURE_DNS_LABEL].[AZURE_LOCATION].azurecontainer.io:[PORT]/awsLambdaCliMavenGraalvmTest`:
```
curl http://aws-lambda-cli-maven-graalvm-test.westeurope.westeurope.azurecontainer.io:8080/awsLambdaCliMavenGraalvmTest
```

## Feature http-client documentation

- [Micronaut HTTP Client documentation](https://docs.micronaut.io/latest/guide/index.html#httpClient)

## Feature aws-lambda-custom-runtime documentation

- [Micronaut Custom AWS Lambda runtime documentation](https://micronaut-projects.github.io/micronaut-aws/latest/guide/index.html#lambdaCustomRuntimes)

- [https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html](https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html)

## Feature aws-lambda documentation

- [Micronaut AWS Lambda Function documentation](https://micronaut-projects.github.io/micronaut-aws/latest/guide/index.html#lambda)

