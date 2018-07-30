## Example AWS IAM policy

This example shows a policy which provides Semaphore with access to manage your
Elastic Beanstalk applications and environments. [This
section](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-using.html#create-managed-policy-console)
of AWS documentation explains how to create a custom policy. You can copy the
policy shown below, but you must update the `[region]` and `[user-or-group-id]` placeholders accordingly for your configuration.

```javascript
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:DeleteObject",
                "s3:GetBucketLocation",
                "s3:GetBucketPolicy",
                "s3:GetObject",
                "s3:GetObjectAcl",
                "s3:GetObjectVersion",
                "s3:ListBucket",
                "s3:ListAllMyBuckets",
                "s3:PutObject",
                "s3:PutObjectAcl",
                "s3:PutObjectVersionAcl"
            ],
            "Resource": [
                "arn:aws:s3:::*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "elasticbeanstalk:CreateApplicationVersion",
                "elasticbeanstalk:DeleteApplicationVersion",
                "elasticbeanstalk:Describe*",
                "elasticbeanstalk:ListAvailableSolutionStacks",
                "elasticbeanstalk:RequestEnvironmentInfo",
                "elasticbeanstalk:UpdateApplicationVersion",
                "elasticbeanstalk:UpdateEnvironment"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudformation:CancelUpdateStack",
                "cloudformation:GetTemplate",
                "cloudformation:Describe*",
                "cloudformation:UpdateStack"
            ],
            "Resource": [
                "arn:aws:cloudformation:[region]:[user-or-group-id]:*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeImages",
                "ec2:DescribeKeyPairs"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "autoscaling:DescribeAutoScalingGroups",
                "autoscaling:DescribeScalingActivities",
                "autoscaling:ResumeProcesses",
                "autoscaling:SuspendProcesses"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "elasticloadbalancing:RegisterInstancesWithLoadBalancer"
            ],
            "Resource": [
                "arn:aws:elasticloadbalancing:*:*:*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "rds:Describe*"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "sns:GetTopicAttributes",
                "sns:ListSubscriptionsByTopic"
            ],
            "Resource": "arn:aws:sns:[region]:[user-or-group-id]:*"
        }
    ]
}
```

Source: https://github.com/renderedtext/semaphore-docs-new/blob/master/source/docs/deploying-to-aws-elastic-beanstalk.md
