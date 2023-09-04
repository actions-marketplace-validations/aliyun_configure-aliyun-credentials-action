# Configure Alibaba Cloud Credentials for GitHub Actions

Configure your Alibaba Cloud credentials environment variables for use in other GitHub Actions.
Environment variable exports are detected by both the Alibaba Cloud SDKs and the Alibaba Cloud CLI for API calls.

## Inputs

### `oidc-provider-arn`

**Optional**: The ARN of OIDC provider. format: `acs:ram::USER_Id:oidc-provider/ROLE_NAME` .

### `role-to-assume`

**Optional**: The ARN of role to assume. format: `acs:ram::USER_Id:role/ROLE_NAME` .

## Outputs

### `aliyun-access-key-id`

The alibaba cloud access key ID for the provided credentials.

### `aliyun-access-key-secret`

The alibaba cloud access key secret for the provided credentials.

### `aliyun-security-token`

The alibaba cloud security token for the provided credentials.

## Example usage

### Using with OIDC

```yaml
uses: actions/configure-aliyun-credentials@v1
with:
  role-to-assume: 'acs:ram::USER_Id:role/ROLE_NAME'
  oidc-provider-arn: 'acs:ram::USER_Id:oidc-provider/ROLE_NAME'
```

### Using with ECS RAM role

If you run your GitHub Actions in a [self-hosted runner](https://help.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners)
that already has configured with RAM role, such as ECS/ECI instance, then you do not need
to provide any credentials to this action.

```yaml
uses: actions/configure-aliyun-credentials@v1
```

When you ant to assume another role, use `role-to-assume` please.

```yaml
uses: actions/configure-aliyun-credentials@v1
with:
  role-to-assume: 'acs:ram::USER_Id:role/ROLENAME'
```

## License Summary

This code is made available under the [MIT license](LICENSE).