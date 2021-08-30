# Security Requirements for Yandex.Cloud configuration

## Network Security
- Virtual machines should be assigned to security groups based on the least privileged principle
- VM group templates should have a security group defined based on the least privileged principle
- Virtual machines are not allowed to assign a public IP address
- The Elasticsearch cluster should be assigned to security group based on the least privileged principle
- The Kafka cluster should be assigned to security group based on the least privileged principle
- The database (ClickHouse, MongoDB, MySQL, PostgreSQL) should be assigned a security group based on the least privileged principle
- The database (ClickHouse, MongoDB, MySQL, PostgreSQL) is not allowed to assign public access
- The bucket (ObjectStorage) should not have rules and policies that allow public access
- Disks, Snapshots, Images should not be publicly available
- Kubernetes cluster should not have a public IP address
- The Kubernetes cluster should be assigned a security group with rules assigned based on the least privileged principle
- Security group should not allow inbound and outbound connections without IP restriction
- Security groups should not allow access from private networks without IP restriction
- The Control Plane of the cluster should be located in a separate VPC from the workers.
- The security group should not contain a range of ports

## Access Control

- AD FS with integrated 2FA should be configured for cloud console access. Cloud administrators and maintainers other than the cloud owner should authenticate to the cloud through this AD FS. (optional)
- The cloud should not have service accounts and system groups with admin rights
- Roles should be assigned according to the principle of the least privileged, excluding the use of the editor role
- All users with edit, admin, owner rights added to Yandex.Cloud (not via AD FS with 2FA) should have two-factor authentication configured into their Yandex account
- Serial console should be disabled
- It is forbidden to store authorization keys in source code. All secrets, keys, passwords, and tokens should be stored in a secure Vault / KMS storage.
- For each task, a separate service account should be created with the minimum required set of privileges. The name of the service account should reflect its tasks and assigned rights when created.
- It is impossible to create API keys (instead of those authorized to obtain an IAM token) without agreement with the IS Department.
- The bucket should not have rules that allow full access, as well as read / write access for all authenticated users

## Logging requirements

- Audit Trails service should be configured for all supported resources.

## Other

- If the bucket contains personal data, banking, or commercial secrets, then encryption should be configured for it
- Versioning should be configured for the bucket
- When creating a Kubernetes cluster in Yandex.Cloud, a network policy should be created based on the principle of the least privileged principle
- The Kubernetes cluster should be configured according to CIS (for configuration that available for change by managed kubernetes).
- It is desirable to configure updates for the cluster

## Marketplace
https://cloud.yandex.com/en-ru/marketplace?categories=security
