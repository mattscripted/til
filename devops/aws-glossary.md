# AWS Glossary

AWS provides a lot of services for cloud computing [<sup>1</sup>](#references).

## General

| Term | Definition |
| - | - |
| **IaaS** | Infrastructure as a Service [<sup>1</sup>](#references) |

## Global Infrastructure

| Term | Definition |
| - | - |
| **Region** | An isolated geographical area containing 2 or more availability zones [<sup>2</sup>](#references) |
| **Availability Zone** | An isolated group of one or more data centers [<sup>2</sup>](#references) |
| **Data Center** | A physical location containing computer systems [<sup>3, 4</sup>](#references) |

## IAM - Identity and Access Management

| Term | Definition |
| - | - |
| **Root** | This account has access to everything and can grant access to everything. _It should not be used._ [<sup>5</sup>](#references) |
| **IAM User** | An individual user with permissions [<sup>5</sup>](#references) |
| **IAM Group** | A collection of IAM users with shared permissions [<sup>5</sup>](#references) |
| **IAM Role** | Delegate access to trusted entities, such as users or servicess [<sup>1, 6</sup>](#references) |
| **IAM Policy** | A document that defines permissions for users, groups, and roles [<sup>1</sup>](#references) |
| **Least Privilege** | Users should only have the minimum privilege necessary to do their tasks [<sup>5</sup>](#references) |

## Services

| Service | Definition |
| - | - |
| **CloudWatch** | Monitoring tool for applications, performance, resources, and operational health [<sup>7</sup>](#references)|
| **EC2** | An EC2 (Elastic Compute Cloud) instance is a virtual server on a virtual machine [<sup>1</sup>](#references) |
| **SNS** | Simple Notificaton Service for sending messages from applications to applications or people [<sup>8</sup>](#references) |

## Pricing

| Term | Definition |
| - | - |
| **Compute** | Amount of resources used such as CPU, RAM, and duration [<sup>1</sup>](#references) |
| **Storage** | Quantity of data stored [<sup>1</sup>](#references) |
| **Outbound Data Transfer** | Quantity of data that is transferred out from all services [<sup>1</sup>](#references) |

## References

1. [YouTube - AWS Basics for Beginners - Full Course by freeCodeCamp.org](https://www.youtube.com/watch?v=ulprqHHWlng)
2. [Rackspace Technology Blog - AWS 101: Regions and Availability Zones](https://www.rackspace.com/blog/aws-101-regions-availability-zones)
3. [AWS - Our Data Centers](https://aws.amazon.com/compliance/data-center/data-centers/)
4. [Wikipedia - Data center](https://en.wikipedia.org/wiki/Data_center)
5. [AWS - IAM - Manage IAM users](https://aws.amazon.com/iam/features/manage-users/)
6. [AWS - IAM - Manage IAM roles](https://aws.amazon.com/iam/features/manage-roles/)
7. [AWS - Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)
8. [AWS - Amazon Simple Notification Service](https://aws.amazon.com/sns/)
