# terraform-aws-state
Initial Infrastructure for managing the Terraform State remotely. 
The Terraform state of this Repository is not stored remotely but locally within this repository.
It does expose some sensitive information, however those are not usable to interact with the state.

To run this Terraform script, it is recommended to have a separate Terraform IAM Group which has access to dynamodb and s3 ressources:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "VisualEditor0",
      "Effect": "Allow",
      "Action": "dynamodb:*",
      "Resource": "arn:aws:dynamodb:*:538138981663:table/*"
    },
    {
      "Sid": "VisualEditor1",
      "Effect": "Allow",
      "Action": "dynamodb:*",
      "Resource": [
        "arn:aws:dynamodb:*:538138981663:table/*/backup/*",
        "arn:aws:dynamodb:*:538138981663:table/*/stream/*",
        "arn:aws:dynamodb::538138981663:global-table/*",
        "arn:aws:dynamodb:*:538138981663:table/*/index/*"
      ]
    },
    {
      "Sid": "VisualEditor2",
      "Effect": "Allow",
      "Action": [
        "dynamodb:ListContributorInsights",
        "dynamodb:DescribeReservedCapacityOfferings",
        "dynamodb:ListGlobalTables",
        "s3:*",
        "dynamodb:ListTables",
        "dynamodb:DescribeReservedCapacity",
        "dynamodb:ListBackups",
        "dynamodb:PurchaseReservedCapacityOfferings",
        "dynamodb:DescribeLimits",
        "dynamodb:ListStreams"
      ],
      "Resource": "*"
    }
  ]
}
```
