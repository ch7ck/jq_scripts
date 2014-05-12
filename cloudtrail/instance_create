#!/usr/bin/env jq -f -c
# Given cloudtrail logs, this selects all audit logs of someone creating an
# instance and prints out who did it, for what instance ID and when.
# Usage:
#   aws s3 cp --recursive \
#       s3://bucketname/AWSLogs/1234567890/CloudTrail/us-east-1/2014/05 .
#   gunzip *.gz
#   ./instance_create.jq *.json
.Records[] |
select(.eventName == "RunInstances") |
[
    .userIdentity.userName,
    .responseElements.instancesSet.items[].instanceId,
    .eventTime
]
