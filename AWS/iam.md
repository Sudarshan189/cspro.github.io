## IAM

### Get existing user
Run the following command to use the GetCallerIdentity API to confirm that the request is running under the root user:

> awslocal sts get-caller-identity

``` json
{
    "UserId": "AKIAIOSFODNN7EXAMPLE",
    "Account": "000000000000",
    "Arn": "arn:aws:iam::000000000000:root"
}
```


### Creating user

 Create a new user named `testUser` using the CreateUser API. Run the following command:

> awslocal iam create-user --user-name testUser

``` json
{
    "User": {
        "Path": "/",
        "UserName": "testUser",
        "UserId": "8qc5xub1llvycwuaov2f",
        "Arn": "arn:aws:iam::000000000000:user/testUser",
        "CreateDate": "2024-07-13T08:32:29.007000Z"
    }
}
```

You can now create an access key pair for the user using the CreateAccessKey API. Run the following command:

> awslocal iam create-access-key --user-name testUser

```json
{
    "AccessKey": {
        "UserName": "testUser",
        "AccessKeyId": "LKIAQAAAAAAAAO37QMNI",
        "Status": "Active",
        "SecretAccessKey": "3ZI/XpPpDgsuXQWQmrxoo+cO1BDIAzjPVHO/MByM",
        "CreateDate": "2024-07-13T08:35:01Z"
    }
}
```

#### You can save the AccessKeyId and SecretAccessKey values, and export them in the environment to run commands under the `testUser` user. Run the following command:

MAC:

> export AWS_ACCESS_KEY_ID=LKIAQAAAAAAAAO37QMNI AWS_SECRET_ACCESS_KEY=3ZI/XpPpDgsuXQWQmrxoo+cO1BDIAzjPVHO/MByM

WINDOWS:
set AWS_ACCESS_KEY_ID=LKIAQAAAAAAAAO37QMNI 
set AWS_SECRET_ACCESS_KEY=3ZI/XpPpDgsuXQWQmrxoo+cO1BDIAzjPVHO/MByM

Verify logged in user is `testUser`

> awslocal sts get-caller-identity

``` json
{
    "UserId": "8qc5xub1llvycwuaov2f",
    "Account": "000000000000",
    "Arn": "arn:aws:iam::000000000000:user/testUser"
}
```